```
ProductSpace{V,T,N,M,S} <: AbstractArray{Chain{V,1,T,N},N}
```

Can be constructed with `\oplus` operation `⊕` and `AbstractRange`,

```julia
julia> (0:0.1:1)⊕(0:0.1:1)
11×11 ProductSpace{⟨_11_⟩, Float64, 2, 2, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}:
...
```

generating a lazy array of `Chain{V,1}` point vectors from the input ranges.

```Julia
Rectangle (alias for ProductSpace{V, T, 2, 2} where {V, T})
Hyperrectangle (alias for ProductSpace{V, T, 3, 3} where {V, T})
RealRegion{V, T} where {V, T<:Real} (alias for ProductSpace{V, T, N, N, S} where {V, T<:Real, N, S<:AbstractArray{T, 1}})
```
