```julia
mutable struct CorrelatedBath <: OpenQuantumBase.AbstractBath
```

`CorrelatedBath`は、その二点相関関数の行列と対応するスペクトルによって相関バスのタイプを定義します。

  * `cfun`: 相関関数
  * `γ`: スペクトル
  * `inds`: バス相関子のインデックス
