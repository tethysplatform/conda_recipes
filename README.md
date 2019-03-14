# Tethys Platform Conda Recipes

This repository contains the conda recipes for various Tethys Platform packages. Each package is on a separate branch of the repository.

## To Create a New Recipe:

1. Clone the master branch of this repository.
2. Create a new branch with the name of the package.
3. Fill in the meta.yaml (see [Conda Build Tutorials](https://conda.io/projects/conda-build/en/latest/user-guide/tutorials/index.html)).
4. If necessary, modify the bld.bat and build.sh scripts (for pure Python packages this is not necessary).
5. Commit changes and submit a Pull Request to contribute recipe.

## To Build the Conda Package

1. Install Anaconda/Miniconda and activate a conda environment of your choice.
2. Install `conda build` per [Install Conda Build](https://conda.io/projects/conda-build/en/latest/install-conda-build.html).
3. Change into the `conda_recipes` directory:

    ```bash
    cd conda_recipes
    ```
4. Run conda build:

    ```bash
    conda-build recipe
    ```
5. Note the location where the package is built for the next step (e.g.: "~/miniconda3/conda-bld/noarch/mypackage-1.0.0-py_0.tar.bz2")

## Uploading Package to `tethysplatform` Channel

1. Install Anaconda Client if necessary:

    ```bash
    conda install anaconda-client
    ```
2. Request access to the `tethysplatform` organization on Anaconda Cloud.
3. Login to Anaconda Cloud (create an account if necessary).

    ```bash
    anaconda login
    ```
4. If package is a noarch package (i.e.: no difference across different platforms or version of python):

    ```bash
    anaconda upload --user tethysplatform <path_to_built_package>
    ```
    
   Otherwise, use the `--all` option to automatically convert the package for different platforms and upload all of them:
   
   ```bash
    anaconda upload --all --user tethysplatform <path_to_built_package>
    ```
