```
ConstraintSatisfactionProblem{T} <: AbstractProblem
```

The abstract base type of constraint satisfaction problems. `T` is the type of the local size of the constraints.

### Required interfaces

  * [`constraints`](@ref), the specification of the constraints. Once the constraints are violated, the size goes to infinity.
  * [`objectives`](@ref), the specification of the size terms as soft constraints, which is associated with weights.

### Optional interfaces

  * [`weights`](@ref): The weights of the soft constraints.
  * [`set_weights`](@ref): Change the weights for the `problem` and return a new problem instance.

### Derived interfaces

  * [`is_satisfied`](@ref), check if the constraints are satisfied.
