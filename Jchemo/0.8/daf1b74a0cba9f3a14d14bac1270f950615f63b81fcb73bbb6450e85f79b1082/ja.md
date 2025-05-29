```
transf(object::Interpl, X)
transf!(object::Interpl, X::Matrix, M::Matrix)
```

モデルから前処理されたデータを計算します。

  * `object` : モデル。
  * `X` : 変換するXデータ。
  * `M` : 事前に割り当てられた出力行列 (n, p)。

インプレース関数は出力を `M` に格納します。
