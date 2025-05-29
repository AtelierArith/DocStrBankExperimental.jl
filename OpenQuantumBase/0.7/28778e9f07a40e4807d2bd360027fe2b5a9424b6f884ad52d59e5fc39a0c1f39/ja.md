```julia
mutable struct CustomBath{lambshift} <: OpenQuantumBase.AbstractBath
```

二点相関関数と対応するスペクトルによって定義されるカスタムバスオブジェクト。

  * `cfun`: 相関関数
  * `γ`: スペクトル
  * `lamb`: ラムシフトS関数
