```
Field(operand::OperationOrFunctionField;
      data = nothing,
      indices = indices(operand),
      boundary_conditions = FieldBoundaryConditions(operand.grid, location(operand)),
      recompute_safely = true)
```

Return a field `f` where `f.data` is computed from `f.operand` by calling `compute!(f)`.

# Keyword arguments

`data` (`AbstractArray`): An offset Array or CuArray for storing the result of a computation.                           Must have `total_size(location(operand), grid)`.

`boundary_conditions` (`FieldBoundaryConditions`): Boundary conditions for `f`.

`recompute_safely` (`Bool`): whether or not to *always* "recompute" `f` if `f` is                              nested within another computation via an `AbstractOperation` or `FunctionField`.                              If `data` is not provided then `recompute_safely=false` and                              recomputation is *avoided*. If `data` is provided, then                              `recompute_safely = true` by default.
