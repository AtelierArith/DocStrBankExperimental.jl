```
make_covariance_matrix(ito_set_::ItoSet, from::Real, to::Real)
```

ItoSetと時間の期間を指定して共分散行列を作成します。これにより、エルミート共分散行列と、この`Hermitian`の軸ラベリングを表すシンボルのベクトルが返されます。

### 入力

  * `ito_set_` - 共分散行列を作成したい`ItoSet`。
  * `from` - 共分散が始まる（数値的な）時間。
  * `to` - 共分散が終了する（数値的な）時間。

### 返り値

  * `Hermitian`共分散行列。
  * 共分散行列のラベルの`Vector{Symbol}`。
