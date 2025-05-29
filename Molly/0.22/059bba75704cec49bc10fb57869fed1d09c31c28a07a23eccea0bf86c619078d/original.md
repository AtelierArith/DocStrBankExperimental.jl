```
ImplicitSolventOBC(atoms, atoms_data, bonds)
```

Onufriev-Bashford-Case GBSA model implemented as an AtomsCalculators.jl calculator.

Should be used along with a [`Coulomb`](@ref) or [`CoulombReactionField`](@ref) interaction. The keyword argument `use_OBC2` determines whether to use parameter set I (`false`, the default) or II (`true`).
