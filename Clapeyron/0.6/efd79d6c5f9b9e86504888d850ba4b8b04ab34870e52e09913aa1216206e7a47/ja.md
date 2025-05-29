```
sle_solubility(model::CompositeModel, p, T, z; solute)
```

与えられた温度と組成で、他の成分の溶液内の各成分の溶解度を計算します。各成分のSLE相境界の組成を含む行列を返します。`solute`が指定されている場合は、指定された成分の溶解度のみを返します。

CompositeModel内で固体および流体モデルが指定されている場合にのみ機能します。
