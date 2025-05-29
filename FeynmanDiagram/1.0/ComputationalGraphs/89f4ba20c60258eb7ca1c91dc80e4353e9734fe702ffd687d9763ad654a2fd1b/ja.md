```
function propagator(ops::Union{OperatorProduct,Vector{QuantumOperator}};
    name="", factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

与えられた OperatorProduct または Vector{QuantumOperator} `ops` から、2 つの量子演算子を含む Propagator 型の FeynmanGraph を作成します。
