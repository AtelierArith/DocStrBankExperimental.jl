```
getinterpolRing(resol::Resolution, θ, ϕ) -> (Array{Int,1}, Array{Float64, 1})
getinterpolRing!(resol::Resolution, θ, ϕ, pix, weights) -> (Array{Int,1}, Array{Float64, 1})
```

指定された解像度のマップにおいて、与えられた方向 (θ, ϕ) の4つの隣接ピクセルのインデックスと重みを返します。

提供された場合、パラメータ `pix` と `weights` はそれぞれ整数と浮動小数点の4要素配列を指す必要があります。これらは、ヒープ割り当てを避け、コードの速度を向上させるために、複数回の呼び出しで再利用できます。
