```
term_type(p::AbstractPolynomialLike)
```

Returns the type of the terms of `p`.

```
term_type(::Type{PT}) where PT<:AbstractPolynomialLike
```

Returns the type of the terms of a polynomial of type `PT`.

```
term_type(p::AbstractPolynomialLike, ::Type{T}) where T
```

Returns the type of the terms of `p` but with coefficient type `T`.

```
term_type(::Type{PT}, ::Type{T}) where {PT<:AbstractPolynomialLike, T}
```

Returns the type of the terms of a polynomial of type `PT` but with coefficient type `T`.
