```
MPValue([T,] 補間, メッシュ)
```

`MPValue` は、基底関数の値やその導関数など、補間のプロパティを格納します。

```jldoctest
julia> mesh = CartesianMesh(1.0, (0,5), (0,5));

julia> xₚ = Vec(2.2, 3.4); # 粒子の位置

julia> mp = MPValue(BSpline(Quadratic()), mesh);

julia> update!(mp, xₚ, mesh) # メッシュ内の位置 `xₚ` で `mp` を更新
MPValue:
  補間: BSpline(Quadratic())
  プロパティ名: w::Matrix{Float64}, ∇w::Matrix{Vec{2, Float64}}
  隣接ノード: CartesianIndices((2:4, 3:5))

julia> sum(mp.w) ≈ 1 # 統一の分割
true

julia> nodeindices = neighboringnodes(mp) # 粒子の局所領域内のグリッドインデックス
CartesianIndices((2:4, 3:5))

julia> sum(eachindex(nodeindices)) do ip # 線形場の再現
           i = nodeindices[ip]
           mp.w[ip] * mesh[i]
       end ≈ xₚ
true
```
