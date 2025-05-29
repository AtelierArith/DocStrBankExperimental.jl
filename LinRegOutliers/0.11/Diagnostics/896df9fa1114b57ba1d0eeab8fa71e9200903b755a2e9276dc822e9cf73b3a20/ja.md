```
mahalanobisSquaredMatrix(data::DataFrame; meanvector=nothing, covmatrix=nothing)
```

マハラノビス距離を計算します。

# 引数

  * `data::DataFrame`: 多変量データのDataFrameオブジェクト。
  * `meanvector::AbstractVector{Float64}`: 変数のオプションの平均ベクトル。
  * `covmatrix::AbstractMatrix{Float64}`: データのオプションの共分散行列。

# 参考文献

マハラノビス、プラサンタ・チャンドラ。「統計における一般化距離について。」インド国立科学研究所、1936年。
