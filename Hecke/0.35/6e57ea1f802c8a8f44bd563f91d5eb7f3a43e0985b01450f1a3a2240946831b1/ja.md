```
structure_constant_algebra(f::PolyRingElem)
```

可換環 $R$ 上の多項式 $f$ に対して、商環 $R[X]/(f)$ を代数として返します。

# 例

```jldoctest
julia> Qx, x = QQ["x"]; f = x^2 - 2;

julia> structure_constant_algebra(f)
Structure constant algebra of dimension 2 over QQ
```
