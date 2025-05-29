```
polynomial_type(p::AbstractPolynomialLike)
```

Returns the type that `p` would have if it was converted into a polynomial.

```
polynomial_type(::Type{PT}) where PT<:AbstractPolynomialLike
```

Returns the same as `polynomial_type(::PT)`.

```
polynomial_type(p::AbstractPolynomialLike, ::Type{T}) where T
```

Returns the type that `p` would have if it was converted into a polynomial of coefficient type `T`.

```
polynomial_type(::Type{PT}, ::Type{T}) where {PT<:AbstractPolynomialLike, T}
```

Returns the same as `polynomial_type(::PT, ::Type{T})`.
