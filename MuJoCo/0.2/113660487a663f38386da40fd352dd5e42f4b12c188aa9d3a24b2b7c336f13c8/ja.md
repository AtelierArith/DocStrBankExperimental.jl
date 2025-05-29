```
mju_cholFactor(mat, mindiag)
```

コレスキー分解: mat = L*L'; ランクを返し、分解はmatにインプレースで実行されます。

# 引数

  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。`mat`は正方行列である必要があります。
  * **`mindiag::Float64`**
