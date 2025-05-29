```
characteristic_polynomial(Vf::QuadSpaceWithIsom) -> QQPolyRingElem
```

Given a quadratic space with isometry $(V, f)$, return the characteristic polynomial of the underlying isometry $f$.

# Examples

```jldoctest
julia> V = quadratic_space(QQ, 2);

julia> Vf = quadratic_space_with_isometry(V; neg=true);

julia> characteristic_polynomial(Vf)
x^2 + 2*x + 1
```
