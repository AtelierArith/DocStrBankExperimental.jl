```
promote_to_field(::Type{T})
```

Promote the type `T` to a field. For instance, `promote_to_field(T)` returns `Rational{T}` if `T` is an integer and `promote_to_field(T)` returns `RationalPoly{T}` if `T` is a polynomial.
