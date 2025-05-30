Apply the static structure factor correction to the given expansion coeffcients.

```julia
ssf_correction(
    coeff,
    Cext,
    Csca;
    volume_fraction,
    r,
    τ,
    Nθ,
    Nm,
    equidistant,
    output_dataframe,
    strategy,
    kwargs...
)

```

  * `coeff`: The original expansion coeffcients, an `(lmax + 1) x 6` matrix.
  * `Cext`: Extinction cross section.
  * `Csca`: Scattering cross section.

Optional parameters:

  * `volume_fraction`: The volume fraction taken by the scatterers. Default is `0.2`.
  * `r`: The volumetrically equivalent/effective radius of the scatterer.
  * `τ`: The stickiness factor. Default is `0`, meaning stickiness is not considered. The valid range is `τ ≥ (2 - √2) / 6`.
  * `Nθ`: Number of angles required for the output scattering matrix. Default is `181`.
  * `Nm`: Number of angles used for the intermediate step. Default is `2lmax`.
  * `equidistant`: Whether or not the output angles should be equidistant. Default is `true`. When set to `false`, Gaussian quadrature nodes (for cosθ) will be used instead.
  * `output_dataframe`: Whether or not to output the scattering matrix in the `DataFrame` format. Default is `false`, and an `Nθ x 6` matrix will be outputed.
  * `strategy`: Special strategy for expansion. Default is `PolarizedBRF.StandardExpansion`, and the expansion can be controlled via the keyword arguments specified for `expand()`. If use `PolarizedBRF.Ito18`, then the strategy used in Ito et al. (2018) will be used instead, in which the highest expansion level is set to `4 * lmax` and the expansion coefficients are cut off at the threshold `1e-8`.
  * All keyword arguments for `expand()` also apply here.
