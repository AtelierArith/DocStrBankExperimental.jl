```
struct OperatorProduct <: AbstractVector{QuantumOperator}

量子演算子の積の構造体です。これは `AbstractVector` のサブタイプであり、
反復やインデックス付けを含む多くのベクトルの動作を継承します。
```

# メンバー:

  * `operators::Vector{QuantumOperator}`  量子演算子のベクトル
