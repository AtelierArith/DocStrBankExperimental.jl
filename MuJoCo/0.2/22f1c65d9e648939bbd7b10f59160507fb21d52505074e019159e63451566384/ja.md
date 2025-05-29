```
mju_sqrMatTD(res, mat, diag)
```

`diag`がNULLでない場合、`res`を`mat' * diag * mat`に設定し、そうでない場合は`res`を`mat' * mat`に設定します。

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res`の行数は`mat`の列数と等しくする必要があります。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。定数。
  * **`diag::Vector{Float64}`** -> **オプション**の可変サイズのベクトル。`diag`は行列ではなくベクトルである必要があります。必要ない場合は`nothing`に設定できます。
