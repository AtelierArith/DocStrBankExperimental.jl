```
structure_constant_algebra(f::PolyRingElem)
```

Given a polynomial $f$ over a commutative ring $R$, return the quotient ring $R[X]/(f)$ as an algebra.

# Examples

```jldoctest
julia> Qx, x = QQ["x"]; f = x^2 - 2;

julia> structure_constant_algebra(f)
Structure constant algebra of dimension 2 over QQ
```
