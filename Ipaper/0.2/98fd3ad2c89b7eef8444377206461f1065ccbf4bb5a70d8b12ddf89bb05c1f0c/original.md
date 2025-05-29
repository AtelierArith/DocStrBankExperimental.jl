to_missing(x::AbstractArray{T}, replacement=0)

to_missing(x::AbstractArray{Union{T,Missing}}, replacement=0)

to_missing!(x::AbstractArray{Union{T,Missing}}, replacement=0)

convert `replacement` to `missing`

```julia
to_missing(
    x::AbstractArray{T<:Real}
) -> Union{CategoricalArrays.CategoricalArray, AbstractArray{Union{Missing, T}} where T<:Real}
to_missing(
    x::AbstractArray{T<:Real},
    replacement
) -> Union{CategoricalArrays.CategoricalArray, AbstractArray{Union{Missing, T}} where T<:Real}

```

# Usage

```julia
to_missing(x)
to_missing(x, replacement)
```

defined at [`packages/Ipaper/NhSLJ/src/missing.jl:29`](file:///home/terasaki/.julia/packages/Ipaper/NhSLJ/src/missing.jl).
