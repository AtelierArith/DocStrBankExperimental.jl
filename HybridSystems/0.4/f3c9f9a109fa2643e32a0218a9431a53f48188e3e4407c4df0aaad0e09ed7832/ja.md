```
GraphAutomaton{GT, ET} <: AbstractAutomaton
```

`Graphs`バックエンドを使用するハイブリッドオートマトンです。コンストラクタ[`GraphAutomaton(::Int)`](@ref)を参照してください。

### フィールド

  * `G` – 状態を決定する頂点を持つ`GT`型のグラフ
  * `Σ` – エッジをそのラベルにマッピングする辞書
