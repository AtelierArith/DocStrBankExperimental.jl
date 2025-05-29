```julia
SpectralTransform(
    ::Type{NF},
    lmax::Integer,
    mmax::Integer,
    nlat_half::Integer;
    Grid,
    ArrayType,
    nlayers,
    LegendreShortcut
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{T, Array, Vector{T1}, Array{Complex{T2}, 1}, Array{Complex{T3}, 2}, Array{Complex{T4}, 3}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{T5, 1, Vector{T6}}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{T7, 2, Matrix{T8}}} where {T, T1, T2, T3, T4, T5, T6, T7, T8}

```

Generator function for a SpectralTransform struct. With `NF` the number format, `Grid` the grid type `<:AbstractGrid` and spectral truncation `lmax, mmax` this function sets up necessary constants for the spetral transform. Also plans the Fourier transforms, retrieves the colatitudes, and preallocates the Legendre polynomials and quadrature weights.
