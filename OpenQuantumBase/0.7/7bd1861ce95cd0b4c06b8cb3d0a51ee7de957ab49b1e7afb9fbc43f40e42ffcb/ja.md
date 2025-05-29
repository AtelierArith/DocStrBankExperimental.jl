```julia
struct Interaction <: OpenQuantumBase.AbstractInteraction
```

カップリング演算子と対応するバスオブジェクトを保持するオブジェクトです。

  * `coupling`: システム演算子
  * `bath`: システム演算子へのバスカップリング
