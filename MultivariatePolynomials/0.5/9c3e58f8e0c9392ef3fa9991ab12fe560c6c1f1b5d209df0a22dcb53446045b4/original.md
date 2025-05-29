```
zero_term(p::AbstractPolynomialLike{T}) where T
```

Equivalent to `constant_term(zero(T), p)`.

```
zero_term(α, ::Type{PT} where {T, PT<:AbstractPolynomialLike{T}}
```

Equivalent to `constant_term(zero(T), PT)`.
