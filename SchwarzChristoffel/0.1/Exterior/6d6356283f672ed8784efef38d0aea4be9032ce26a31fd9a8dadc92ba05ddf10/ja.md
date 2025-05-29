```
moments(m::ExteriorMap) -> Vector{ComplexF64}
```

外部多角形写像 `m` の前頂点のモーメントを返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> mom = moments(m);
```
