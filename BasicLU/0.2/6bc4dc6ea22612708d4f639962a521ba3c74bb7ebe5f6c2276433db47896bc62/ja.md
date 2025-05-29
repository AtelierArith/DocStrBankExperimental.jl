```
basis, F = maxvolbasis(A::SparseMatrixCSC{Float64, Int64}; lindeptol::Float64=1e-8,
                       volumetol::Float64=2.0, maxpass::Int64=2, verbose::Bool=true) -> Vector{Int64}, LUFactor
```

行列 `AI = [A I]` の列インデックスのセットを見つけます。ここで `AI[:,basis]` は正方行列で非特異であり、基底におけるスラック列の数が最小になるようにします（これは `A` の行ランク欠損です）。基底行列を形成する `AI` の列インデックスのベクトルと、基底行列の因子分解を保持する `LUFactor` を返します。

方法: `AI` のスラック列を `lindeptol` でスケールし、この行列の最大体積基底を見つけるために、[`maxvolume`](@ref) への呼び出しを最大 `maxpass` 回行います。`verbose` が true の場合、各呼び出し後の基底更新の数を印刷します。
