```
update!(sc::SimpleCovariance, from::Real, to::Real)
```

これは `SimpleCovariance` を取り、新しい時間の範囲に対して更新します。新しい時間の範囲は from と to の間です。`SimpleCovariance` の場合、これは新しい時間範囲に対して共分散を調整することで行われます（対応する調整を伴って）チョレスキー、逆行列などに。

`ForwardCovariance`（これは `StochasticIntegralsCovariance` でもあります）に対する対応する手法は、新しい `ForwardCovariance` コンストラクタにそれを渡し、新しい範囲のために再計算させることです。

### 入力

  * `sc` - `SimpleCovariance` 構造体。
  * `from` - 共分散を求めたい時間。
  * `to` - 共分散を求めたい時間。

### 戻り値

何も返しません。入力として渡した sc 構造体を更新するだけです。
