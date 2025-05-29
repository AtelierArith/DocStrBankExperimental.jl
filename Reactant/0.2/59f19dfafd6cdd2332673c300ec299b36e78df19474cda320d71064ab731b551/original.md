```
DotGeneralAlgorithm(
    ::Type{lhsT}, ::Type{rhsT}, ::Type{accumT},
    rhs_component_count::Int, lhs_component_count::Int, num_primitive_operations::Int,
    allow_imprecise_accumulation::Bool
)
DotGeneralAlgorithm{lhsT,rhsT,accumT}(
    lhs_component_count::Int, rhs_component_count::Int, num_primitive_operations::Int,
    allow_imprecise_accumulation::Bool
)
```

Represents the configuration of the `stablehlo.dot_general` operation.

# Arguments

  * `lhsT`: The type of the left-hand side operand.
  * `rhsT`: The type of the right-hand side operand.
  * `accumT`: The type of the accumulation operand.
  * `lhs_component_count`: The number of components in the left-hand side operand.
  * `rhs_component_count`: The number of components in the right-hand side operand.
  * `num_primitive_operations`: The number of primitive operations in the `stablehlo.dot_general` operation.
