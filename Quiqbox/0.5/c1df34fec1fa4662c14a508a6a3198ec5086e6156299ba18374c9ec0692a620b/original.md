```
flatten(bs::AbstractVector{<:GTBasisFuncs{T, D}}) where {T, D} -> 
AbstractVector{<:GTBasisFuncs{T, D, 1}}

flatten(bs::Tuple{Vararg{GTBasisFuncs{T, D}}}) where {T, D} -> 
Tuple{Vararg{GTBasisFuncs{T, D, 1}}}
```

Flatten a collection of `GTBasisFuncs` by decomposing every `GTBasisFuncs{T, D, ON}`  where `ON > 1` into multiple `GTBasisFuncs{T, D, 1}`.
