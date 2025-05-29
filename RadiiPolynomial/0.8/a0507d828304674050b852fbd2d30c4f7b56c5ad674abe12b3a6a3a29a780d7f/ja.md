```
×(::VectorSpace, ::VectorSpace)
×(::CartesianProduct, ::CartesianProduct)
×(::CartesianProduct, ::VectorSpace)
×(::VectorSpace, ::CartesianProduct)
```

いくつかの [`VectorSpace`](@ref) の直積から [`CartesianProduct`](@ref) を作成します。

関連情報: [`CartesianProduct`](@ref), [`CartesianPower`](@ref) および [`^(::VectorSpace, ::Int)`](@ref)。

# 例

```jldoctest
julia> Taylor(1) × Fourier(2, 1.0)
Taylor(1) × Fourier(2, 1.0)

julia> Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)
Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)

julia> (Taylor(1) × Fourier(2, 1.0)) × Chebyshev(3)
Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)

julia> Taylor(1) × (Fourier(2, 1.0) × Chebyshev(3))
Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)

julia> ParameterSpace()^2 × ((Taylor(1) ⊗ Fourier(2, 1.0)) × Chebyshev(3))^3
𝕂² × ((Taylor(1) ⊗ Fourier(2, 1.0)) × Chebyshev(3))³
```
