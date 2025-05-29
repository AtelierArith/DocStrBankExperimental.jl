```
basetype(::Type{TN}) where TN<:ThickNumber
```

Strip the `valuetype` from `TN`.

# Interface requirements

`basetype` must be implemented by all ThickNumber subtypes.

# Examples

In a package implementing `Interval` you would define

```julia
ThickNumbers.basetype(::Type{Interval{T}}) where T = Interval
ThickNumbers.basetype(::Type{Interval}) = Interval
```

so that

```julia
julia> basetype(Interval{Float64})
Interval
```

This can be used to construct `valuetype`-agnostic ThickNumbers:

```julia
julia> lohi(basetype(Interval{Float64}), 1, 2))
Interval{Int64}(1, 2)
```
