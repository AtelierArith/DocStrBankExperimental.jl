to_missing(x::AbstractArray{T}, replacement=0)

to_missing(x::AbstractArray{Union{T,Missing}}, replacement=0)

to_missing!(x::AbstractArray{Union{T,Missing}}, replacement=0)

`replacement`を`missing`に変換します

```julia
to_missing(
    x::AbstractArray{T<:Real}
) -> Union{CategoricalArrays.CategoricalArray, AbstractArray{Union{Missing, T}} where T<:Real}
to_missing(
    x::AbstractArray{T<:Real},
    replacement
) -> Union{CategoricalArrays.CategoricalArray, AbstractArray{Union{Missing, T}} where T<:Real}

```

# 使用法

```julia
to_missing(x)
to_missing(x, replacement)
```

[`packages/Ipaper/NhSLJ/src/missing.jl:29`](file:///home/terasaki/.julia/packages/Ipaper/NhSLJ/src/missing.jl)で定義されています。
