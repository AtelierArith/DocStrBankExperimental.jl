```
mju_cholFactorBand(mat, ntotal, nband, ndense, diagadd, diagmul)
```

バンド密なコレスキー分解。因子化された対角線の最小値を返すか、ランクが不足している場合は0を返します。matは(ntotal-ndense) x nband + ndense x ntotal要素を持っています。最初の(ntotal-ndense) x nbandは対角線の左側にあるバンド部分を格納します。2番目のndense x ntotalは、バンド部分を完全な密な行として格納します。因子化の前に対角線にdiagadd+diagmul*mat_iiを加えます。

# 引数

  * **`mat::Vector{Float64}`** -> 可変サイズのベクトル。`mat`はベクトルであるべきで、行列ではありません。
  * **`ntotal::Int32`**
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`diagadd::Float64`**
  * **`diagmul::Float64`**
