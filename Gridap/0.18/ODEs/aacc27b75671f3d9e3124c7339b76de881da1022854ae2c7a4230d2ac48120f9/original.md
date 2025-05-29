```
evaluate!(
  transient_space::FESpace,
  space::TransientTrialFESpace, t::Real
) -> FESpace
```

Replace the Dirichlet values of the space by those at time `t`.
