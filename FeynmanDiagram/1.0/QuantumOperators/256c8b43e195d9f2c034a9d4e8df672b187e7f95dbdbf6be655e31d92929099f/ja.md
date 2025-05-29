```
struct QuantumOperator
```

量子演算子の構造体。

# メンバー:

  * `operator::Datatype`: 量子演算子の型、:f⁺、:f⁻、:f、:b⁺、:b⁻、:ϕをサポート。
  * `label::Int`: 演算子インデックスのラベル。時空、スピン、運動量、フレーバーなどを表すことができる。
  * `is_ghost::Bool`: 演算子がゴースト演算子であるかどうか。
