```julia
struct TimeDependentCouplings <: OpenQuantumBase.AbstractTimeDependentCouplings
```

時間依存のシステムバス結合演算子の1次元配列を定義します。

# フィールド

  * `coupling`: 単一の `TimeDependentCoupling` 演算子のタプル
