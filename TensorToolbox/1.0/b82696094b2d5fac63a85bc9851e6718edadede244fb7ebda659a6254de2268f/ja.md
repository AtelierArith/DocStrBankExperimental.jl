```
hosvd(X; <キーワード引数>)
```

高次元特異値分解。

## 引数:

  * `X`: テンソル（多次元配列）または ttensor。
  * `method` ∈ {"svd","lanczos","randsvd"} SVDの方法。デフォルト: "svd"。
  * `reqrank::Vector`: 要求される多重線形ランク。オプション。
  * `eps_abs::Number/Vector`: eps_abs未満の特異値（モード-n 行列化）をドロップします。デフォルト: 1e-8。
  * `eps_rel::Number/Vector`: eps*rel*sigma*1未満の特異値（モード-n 行列化）をドロップします。オプション。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト p=10。
