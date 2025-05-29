```
coefficients(m::ConformalMap) -> Tuple{Vector{ComplexF64},Vector{ComplexF64}}
```

`m`によって記述された写像$z(\zeta)$の多極展開の複素係数のベクトルのタプルと、写像の平方の大きさ$|z(\zeta)|^2$の係数を返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> ccoeff, dcoeff = coefficients(m);
```
