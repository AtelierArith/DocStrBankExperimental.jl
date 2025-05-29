```
MixedCell
```

混合セルを表すデータ構造。

## フィールド

  * `indices::Vector{NTuple{2, Int}}`: 混合セルを作成するサポートの列。
  * `normal::Vector{Float64}`: リフトされた混合セルの内法線ベクトル。
  * `β::Vector{Float64}`: ベクトル $(\min_{a \in A_i} ⟨a,γ⟩)_i$ で、$γ$ は `normal` です。
  * `volume::Int`: 混合セルの体積。
