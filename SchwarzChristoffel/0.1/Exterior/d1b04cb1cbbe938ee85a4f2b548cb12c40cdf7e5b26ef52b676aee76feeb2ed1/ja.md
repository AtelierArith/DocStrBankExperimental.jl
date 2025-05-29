```
parameters(m::ExteriorMap) -> Tuple{Vector{ComplexF64},ComplexF64}
```

外部多角形マッピング `m` の前頂点のベクトルと複素数因子のタプルを返します。

# 例

```jldoctest paramtest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> prev, C = parameters(m);

julia> prev
4-element Array{Complex{Float64},1}:
       1.0+0.0im
  0.376406-0.926455im
 -0.902383-0.430935im
 -0.186756+0.982406im
```
