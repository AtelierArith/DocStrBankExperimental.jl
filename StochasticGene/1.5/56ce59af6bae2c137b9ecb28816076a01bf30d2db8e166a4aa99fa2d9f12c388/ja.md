```
predictedarray(r, data::RNAData{T1,T2}, model::AbstractGMmodel) where {T1<:Array, T2<:Array}
```

複数のヒストグラムの尤度を計算し、PDFの配列を返します。

# 引数

  * `r`: レート。
  * `data::RNAData{T1,T2}`: RNAデータ。
  * `model::AbstractGMmodel`: モデル。

# 戻り値

  * `Array{Array{Float64,1},1}`: ヒストグラムのPDFの配列。
