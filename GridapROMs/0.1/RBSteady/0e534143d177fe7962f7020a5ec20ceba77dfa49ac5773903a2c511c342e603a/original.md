```
abstract type RBSpace <: FESpace end
```

Represents a vector subspace of a `FESpace`.

Subtypes:

  * [`SingleFieldRBSpace`](@ref)
  * [`MultiFieldRBSpace`](@ref)
  * [`EvalRBSpace`](@ref)
