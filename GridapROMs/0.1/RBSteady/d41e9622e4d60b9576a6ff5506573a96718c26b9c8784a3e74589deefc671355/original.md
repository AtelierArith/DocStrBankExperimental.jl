```
abstract type RBOperator{O} <: ParamOperator{O,SplitDomains} end
```

Type representing reduced algebraic operators used within a reduced order modelling framework in steady applications. A RBOperator should contain the following information:

  * a reduced test and trial space, computed according to [`reduced_spaces`](@ref)
  * a hyper-reduced residual and jacobian, computed according to [`reduced_weak_form`](@ref)

Subtypes:

  * [`GenericRBOperator`](@ref)
  * [`LinearNonlinearRBOperator`](@ref)
