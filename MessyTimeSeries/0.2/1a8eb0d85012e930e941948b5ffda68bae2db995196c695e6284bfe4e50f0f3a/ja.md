```
lag(X::FloatArray, p::Int64)
```

標準的なベクトル自己回帰を実行するために必要なデータを構築します。

# 引数

  * `X`: 観測された測定値（`nxT`）、ここで `n` は系列の数、`T` は観測の数です。
  * `p`: ベクトル自己回帰におけるラグの数

# 出力

  * `X_{t}`
  * `X_{t-1}`
