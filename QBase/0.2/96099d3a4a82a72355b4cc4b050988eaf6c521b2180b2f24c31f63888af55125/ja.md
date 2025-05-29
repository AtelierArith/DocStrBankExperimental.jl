```
abstract type Operator{T<:Number} <: AbstractMatrix{Number} end
```

複素値ヒルベルト空間に作用する線形演算子を表す行列です。`Operator`は量子力学におけるすべての線形演算子の親となる抽象型です。これらの行列型は、量子状態、進化、測定を表すことができ、それぞれに個別の制約があります。これらの制約は`Operator`抽象型の子供に課せられます。
