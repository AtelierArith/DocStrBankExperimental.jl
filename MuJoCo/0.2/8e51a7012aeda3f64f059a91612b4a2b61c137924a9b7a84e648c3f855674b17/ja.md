```
mju_symmetrize(res, mat)
```

行列 res = (mat + mat')/2 を対称化します。

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res` と mat は同じ形状である必要があります。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。`mat` は正方行列である必要があります。res と `mat` は同じ形状である必要があります。定数。
