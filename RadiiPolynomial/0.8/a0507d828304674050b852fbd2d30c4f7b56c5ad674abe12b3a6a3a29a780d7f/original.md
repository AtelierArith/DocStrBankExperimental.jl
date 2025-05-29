```
×(::VectorSpace, ::VectorSpace)
×(::CartesianProduct, ::CartesianProduct)
×(::CartesianProduct, ::VectorSpace)
×(::VectorSpace, ::CartesianProduct)
```

Create a [`CartesianProduct`](@ref) from the cartesian product of some [`VectorSpace`](@ref).

See also: [`CartesianProduct`](@ref), [`CartesianPower`](@ref) and [`^(::VectorSpace, ::Int)`](@ref).

# Examples

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
