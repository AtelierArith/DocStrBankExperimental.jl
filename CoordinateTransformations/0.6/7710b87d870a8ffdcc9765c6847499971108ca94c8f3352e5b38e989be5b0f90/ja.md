```
Spherical(r, θ, ϕ)
```

3D球面座標

球面座標の規約は多く存在し、このライブラリではやや異なるものを使用しています。直交座標 `xyz` を持つベクトル `v` が与えられたとき、`v_xy = [x,y,0]` は `v` の `xy` 平面への直交投影です。

  * `r` は半径です。`norm(v, 2)` によって与えられます。
  * `θ` は方位角です。`x` 軸から `v_xy` への角度です。
  * `ϕ` は緯度です。`v_xy` から `v` への角度です。

```jldoctest
julia> v = randn(3);

julia> sph = SphericalFromCartesian()(v);

julia> r = sph.r; θ = sph.θ; ϕ = sph.ϕ;

julia> v ≈ [r * cos(θ) * cos(ϕ), r * sin(θ) * cos(ϕ), r * sin(ϕ)]
true
```
