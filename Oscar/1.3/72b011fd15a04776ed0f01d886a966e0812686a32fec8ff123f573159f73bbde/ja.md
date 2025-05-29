```
characteristic_polynomial(Vf::QuadSpaceWithIsom) -> QQPolyRingElem
```

与えられた同型を持つ二次空間 $(V, f)$ に対して、基礎となる同型 $f$ の特性多項式を返します。

# 例

```jldoctest
julia> V = quadratic_space(QQ, 2);

julia> Vf = quadratic_space_with_isometry(V; neg=true);

julia> characteristic_polynomial(Vf)
x^2 + 2*x + 1
```
