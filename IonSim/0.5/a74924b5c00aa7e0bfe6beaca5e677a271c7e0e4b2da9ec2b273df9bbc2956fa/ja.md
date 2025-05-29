```
matrixelement(ion::Ion, transition::Tuple, I::Real, ϵhat::NamedTuple, khat::NamedTuple, Bhat::NamedTuple=(;z=1))
```

二つのエネルギーサブレベル間の行列要素（Hz単位）を計算します **args**

  * `ion`: 遷移を行うイオン
  * `transition`: 遷移が計算されるサブレベルのタプル（フルネームまたはエイリアス）。`energy(transition[2]) > energy(transition[1])` の形式である必要があります。
  * `I`: 駆動場の強度
  * `ϵhat`: 光の偏光の単位ベクトル
  * `khat`: 光の波ベクトルの単位ベクトル
  * `Bhat`: 磁場の単位ベクトル
