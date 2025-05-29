```
quadratic_field(d::IntegerUnion) -> AbsSimpleNumField, AbsSimpleNumFieldElem
```

Returns the field with defining polynomial $x^2 - d$.

# Examples

```jldoctest
julia> quadratic_field(5)
(Real quadratic field defined by x^2 - 5, sqrt(5))
```
