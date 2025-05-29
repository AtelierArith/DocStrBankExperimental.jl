```julia
∇²!(
    ∇²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    add,
    flipsign,
    inverse,
    radius
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Laplace operator ∇² applied to the spectral coefficients `alms` in spherical coordinates. The eigenvalues which are precomputed in `S`. ∇²! is the in-place version which directly stores the output in the first argument `∇²alms`. Acts on the unit sphere, i.e. it omits any radius scaling as all inplace gradient operators, unless the `radius` keyword argument is provided.

# Keyword arguments

  * `add=true` adds the ∇²(alms) to the output
  * `flipsign=true` computes -∇²(alms) instead
  * `inverse=true` computes ∇⁻²(alms) instead

Default is `add=false`, `flipsign=false`, `inverse=false`. These options can be combined.
