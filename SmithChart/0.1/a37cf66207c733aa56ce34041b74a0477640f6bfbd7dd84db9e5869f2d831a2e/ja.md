```
StabilityCircle(S11, S12, S21, S22, inout::Symbol, Np; stable = false)
```

安定性（または不安定性）の領域を計算し、Makie.Polygonを返します。

  * Sii: Sパラメータ
  * inout: ソースまたは負荷領域を選択するシンボル。 有効な値は:loadまたは:sourceです。
  * Np: ポイントの数。
  * stable: 領域が安定（true）または不安定（false）領域に対応するかを選択します。
