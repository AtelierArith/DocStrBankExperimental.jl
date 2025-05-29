```
InverseMap(m::ConformalMap)
```

与えられた準同型写像 `m` の逆準同型写像を構築します。

この逆準同型写像は、単一の点または点のベクトルで評価できます。点は体の外にある必要があります。円平面内の結果の点が円の内側または外側として解釈されるかどうかは、オプションの引数 `inside` によって決まります。デフォルトは `false` です。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> m⁻¹ = InverseMap(m);

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.1+1.1im];

julia> m⁻¹(m(ζ))
3-element Array{Complex{Float64},1}:
  1.0+3.0im
 -2.0-2.0im
  0.1+1.1im
```
