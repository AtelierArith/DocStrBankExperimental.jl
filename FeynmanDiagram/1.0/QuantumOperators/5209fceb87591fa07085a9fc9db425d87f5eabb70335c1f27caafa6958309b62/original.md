```
struct OperatorProduct <: AbstractVector{QuantumOperator}

struct of a quantum-operator product. It is a subtype of `AbstractVector` and
inherits a large set of Vector behaviors including iteration and indexing.
```

# Members:

  * `operators::Vector{QuantumOperator}`  vector of quantum operators
