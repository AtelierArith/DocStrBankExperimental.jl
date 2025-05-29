```
colspace(X; <keyword arguments>)
```

列空間基底。

## 引数:

  * `X`: 行列。
  * `method` ∈ {"svd","lanczos","randsvd"} SVDのためのメソッド。デフォルト: "svd"。
  * `maxrank::Integer`: 最大ランク。オプション。
  * `atol::Number`: atol未満の特異値を除外します。デフォルト: 1e-8。
  * `rtol::Number`: rtol*sigma_1未満の特異値を除外します。オプション。
  * `p::Integer`: lanczosおよびrandsvdメソッドで使用されるオーバーサンプリングパラメータ。デフォルト p=10。
