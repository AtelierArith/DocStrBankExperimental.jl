```julia
ItemIntegrator(
    operators;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, Float64, ON_CELLS, Float64, Int32, GradientRobustMultiPhysics.NoAction}
ItemIntegrator(
    operators,
    action;
    T,
    AT,
    regions,
    name
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, Float64, ON_CELLS, Float64, Int32}

```

Creates an ItemIntegrator assembly pattern based on:

  * operators : operators that should be evaluated for the coressponding FESpace (last one refers to test function)
  * action    : an Action with kernel of interface (result, input, kwargs) that takes input (= all but last operator evaluations) and computes result to be dot-producted with test function evaluation             (if no action is specified, the full input vector is dot-producted with the test function operator evaluation)

Optional arguments:

  * T         : expected NumberType for evaluation output
  * AT        : specifies on which entities of the grid the ItemINtegrator is evaluated
  * regions   : specifies in which regions the operator should assemble, default [0] means all regions
  * name      : name for this LinearForm that is used in print messages
