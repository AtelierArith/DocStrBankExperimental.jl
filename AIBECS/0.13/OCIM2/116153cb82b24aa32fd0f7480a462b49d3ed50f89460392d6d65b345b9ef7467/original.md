This `OCIM2` module is used to load the OCIM2 matrices and grid for use in AIBECS.

!!! tip
    To load the default OCIM2 matrix and grid, do

    ```
    julia> grd, T = OCIM2.load()
    ```

    But you can also load the other matrices by specifying which version you want, e.g.,

    ```
    julia> grd, T = OCIM2.load(version="OCIM2_KiHIGH_noHe")
    ```

    See *DeVries and Holzer* (2019) for more details


!!! note
    The files, that are downloaded from a public and persistant URL in FigShare, were created with the code available at https://github.com/briochemc/OceanCirculations.

