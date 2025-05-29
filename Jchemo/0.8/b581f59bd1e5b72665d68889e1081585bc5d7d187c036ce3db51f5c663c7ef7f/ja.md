```
transf(object::Fdif, X)
transf!(object::Fdif, X::Matrix, M::Matrix)
```

モデルから前処理されたデータを計算します。

  * `object` : モデル。
  * `X` : 変換するXデータ。
  * `M` : 事前に割り当てられた出力行列 (n, p - npoint + 1)。

インプレース関数は出力を `M` に格納します。
