This `OCIM2_48L` module is used to load the OCIM2-48L matrices and grid for use in AIBECS.

!!! tip
    To load the default OCIM2_48L matrix and grid, do

    ```
    julia> grd, T = OCIM2_48L.load()
    ```

    But you can also load the other matrices by specifying which version you want, e.g.,

    ```
    julia> grd, T = OCIM2_48L.load(version="OCIM2_48L_KiHIGH_noHe")
    ```

    See *DeVries and Holzer* (2019) for more details


!!! note
    The files, that are downloaded from a public and persistant URL in FigShare, were created with the code available at https://github.com/briochemc/OceanCirculations.

