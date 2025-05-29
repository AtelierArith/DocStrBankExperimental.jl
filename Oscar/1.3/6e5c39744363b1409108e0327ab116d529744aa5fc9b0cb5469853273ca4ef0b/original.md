```
characteristic_polynomial(M::Matroid)
characteristic_polynomial(M::Matroid; parent::ZZPolyRing)
characteristic_polynomial(parent::ZZPolyRing, M::Matroid)
```

Return the characteristic polynomial of `M`. This is polynomial in the variable q with integral coefficients. It is computed as an evaluation of the Tutte polynmomial. See Section 15.2 in [Oxl11](@cite).

# Examples

```jldoctest
julia> characteristic_polynomial(fano_matroid())
q^3 - 7*q^2 + 14*q - 8

```
