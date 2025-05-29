```
struct QuantumOperator
```

struct of a quantum operator.

# Members:

  * `operator::Datatype`: type of quantum operator, supports :f⁺, :f⁻, :f, :b⁺, :b⁻, :ϕ
  * `label::Int`:  label of the operator indices. It could represent spacetime, spin, momentum, flavor, etc.
  * `is_ghost::Bool`: whether the operator is a ghost operator or not.
