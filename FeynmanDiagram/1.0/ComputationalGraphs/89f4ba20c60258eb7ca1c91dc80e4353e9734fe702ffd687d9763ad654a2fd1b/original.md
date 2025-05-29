```
function propagator(ops::Union{OperatorProduct,Vector{QuantumOperator}};
    name="", factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

Create a Propagator-type FeynmanGraph from given OperatorProduct or Vector{QuantumOperator} `ops`, including two quantum operators.
