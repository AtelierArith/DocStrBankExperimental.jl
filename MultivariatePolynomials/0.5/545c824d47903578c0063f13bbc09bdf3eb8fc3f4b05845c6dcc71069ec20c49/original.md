```
coefficient_type(p::AbstractPolynomialLike)
```

Returns the coefficient type of `p`.

```
coefficient_type(::Type{PT}) where PT
```

Returns the coefficient type of a polynomial of type `PT`.

### Examples

Calling `coefficient_type` on $(4//5)x^2y$ should return `Rational{Int}`, calling `coefficient_type` on $1.0x^2y + 2.0x$ should return `Float64` and calling `coefficient_type` on $xy$ should return `Int`.
