```
mju_cholUpdate(mat, x, flg_plus)
```

コレスキーランク1更新: L*L' +/- x*x'; ランクを返す。

# 引数

  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。`mat` は正方行列である必要があります。
  * **`x::Vector{Float64}`** -> 可変サイズのベクトル。`x` は行列ではなくベクトルである必要があります。
  * **`flg_plus::Int32`**
