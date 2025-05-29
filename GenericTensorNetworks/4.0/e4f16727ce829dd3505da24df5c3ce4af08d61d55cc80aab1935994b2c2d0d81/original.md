```julia
struct GenericTensorNetwork{CFG, CT, LT}
```

```
GenericTensorNetwork(problem::ConstraintSatisfactionProblem; openvertices=(), fixedvertices=Dict(), optimizer=GreedyMethod())
```

The generic tensor network that generated from a [`ConstraintSatisfactionProblem`](@ref).

## Positional arguments

  * `problem` is the graph problem.
  * `code` is the tensor network contraction code.
  * `fixedvertices` is a dictionary specifying the fixed dimensions.
