Calculate scattering matrix for given angles using the expansion coefficients.

```julia
F_from_expansion(coeff, θ; output_dataframe, data)

```

  * `coeff`: Expansion coefficients, which is an `lmax1 x 6` matrix.
  * `θ`: The angles in ascending order at which the scattering matrix is calculated.

Optional parameters:

  * `output_dataframe`: Whether or not to output the scattering matrix in the `DataFrame` format. Default is `false`, and an `Nθ x 6` matrix will be outputed.
  * `data`: Use precalculated Wigner d data. By default new data will be calculated.
