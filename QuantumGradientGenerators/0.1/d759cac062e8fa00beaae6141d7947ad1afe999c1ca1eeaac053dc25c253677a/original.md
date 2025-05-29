Static generator for the dynamic gradient.

```julia
using QuantumPropagators.Controls: evaluate

G::GradgenOperator = evaluate(gradgen::GradGenerator; vals_dict)
```

is the result of plugging in specific values for all controls in a [`GradGenerator`](@ref).

The resulting object can be multiplied directly with a [`GradVector`](@ref), e.g., in the process of evaluating a piecewise-constant time propagation.
