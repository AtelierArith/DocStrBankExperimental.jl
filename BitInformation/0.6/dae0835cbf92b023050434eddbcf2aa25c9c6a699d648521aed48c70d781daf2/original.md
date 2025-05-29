```
M = bitinformation(A::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

Bitwise real information content of array `A` calculated from the bitwise mutual information in adjacent entries in `A`. Optional keyword arguments

```
- `dim::Int=1` computes the bitwise information along dimension `dim`.
- `masked_value::T=NaN` masks all entries in `A` that are equal to `masked_value`.
- `set_zero_insignificant::Bool=true` set insignificant information to zero.
- `confidence::Real=0.99` confidence level for `set_zero_insignificant`.
```
