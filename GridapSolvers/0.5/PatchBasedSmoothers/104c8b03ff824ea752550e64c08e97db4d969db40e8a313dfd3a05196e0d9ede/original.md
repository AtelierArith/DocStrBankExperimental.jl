```
function PatchBasedLinearSolver(
  biform::Function, 
  patch_space::FESpace, 
  space::FESpace;
  local_solver = LUSolver(),
  is_nonlinear = false,
  weighted = false
)
```

Returns an instance of [`PatchBasedLinearSolver`](@ref) from its underlying properties.   Local patch-systems are solved with `local_solver`. If `weighted`, uses weighted    patch aggregation to compute the global correction.
