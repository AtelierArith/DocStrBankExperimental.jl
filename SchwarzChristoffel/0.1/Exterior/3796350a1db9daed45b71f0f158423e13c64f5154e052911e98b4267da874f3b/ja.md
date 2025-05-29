```
DerivativeMap(m::ConformalMap)
```

与えられた準同型写像 `m` の一次および二次導関数から新しい準同型写像を構築します。

これらの新しい準同型写像は、`m` と同様に単一またはベクトルの点で評価できます。返されるタプルの最初のエントリは一次導関数で、二番目のエントリは二次導関数です。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> dm = DerivativeMap(m);

julia> ζ = [0.1,0.5-0.75im,-0.25-0.3im];

julia> dz, ddz = dm(ζ;inside=true);

julia> dz
3-element Array{Complex{Float64},1}:
  67.2068+76.6284im
 -1.11666+0.544576im
  3.99129-5.30641im
```
