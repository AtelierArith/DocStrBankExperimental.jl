```
transfermatrix(iv::InvariantMeasure) → (M::AbstractArray{<:Real, 2}, bins::Vector{<:SVector})
```

転送行列/演算子と対応するビンを返します。ここで、`bins[i]`は転送行列のi番目の行/列に対応します。したがって、エントリ`M[i, j]`は、`bins[i]`で定義された状態から`bins[j]`で定義された状態にジャンプする確率です。

関連情報: [`TransferOperator`](@ref).
