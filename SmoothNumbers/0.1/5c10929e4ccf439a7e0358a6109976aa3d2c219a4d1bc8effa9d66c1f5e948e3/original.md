```
with_bases(bases::AbstractVector{T}, n::Integer) where T<:Integer
```

Computes the first `n` numbers that can be written as a product of powers of the `bases`.

The result is a `Vector` with the same element type as `bases`.
