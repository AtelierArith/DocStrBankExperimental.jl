```
ExtendedTropical{K,TO} <: Number
ExtendedTropical{K}(orders)
```

Extended Tropical numbers with largest `K` orders keeped, or the [`TruncatedPoly`](@ref) without coefficients, `TO` is the element type of orders, usually [`Tropical`](@ref) numbers. This algebra maps

  * `+` to finding largest `K` values of union of two sets.
  * `*` to finding largest `K` values of sum combination of two sets.
  * `0` to set [-Inf, -Inf, ..., -Inf, -Inf]
  * `1` to set [-Inf, -Inf, ..., -Inf, 0]

## Fields

  * `orders` is a vector of [`Tropical`](@ref) ([`CountingTropical`](@ref)) numbers as the largest-K solution sizes (solutions).

## Examples

```jldoctest; setup=(using GenericTensorNetworks)
julia> x = ExtendedTropical{3}(Tropical.([1.0, 2, 3]))
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[1.0ₜ, 2.0ₜ, 3.0ₜ])

julia> y = ExtendedTropical{3}(Tropical.([-Inf, 2, 5]))
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, 2.0ₜ, 5.0ₜ])

julia> x * y
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[6.0ₜ, 7.0ₜ, 8.0ₜ])

julia> x + y
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[2.0ₜ, 3.0ₜ, 5.0ₜ])

julia> one(x)
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, -Infₜ, 0.0ₜ])

julia> zero(x)
ExtendedTropical{3, Tropical{Float64}}(Tropical{Float64}[-Infₜ, -Infₜ, -Infₜ])
```
