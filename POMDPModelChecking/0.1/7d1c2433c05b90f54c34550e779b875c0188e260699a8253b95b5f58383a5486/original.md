```
ModelCheckingSolver
```

A probabilistic model checker for MDPs and POMDPs with LTL specification.  The solver takes as input an LTL formula and the underlying MDP/POMDP planning algorithm used to perform the model checking.  It supports any solver from POMDPs.jl.  Internally, this solver requires a discrete state and discrete action model.

# Fields

  * `property::SpotFormula`
  * `solver::Solver` any MDP/POMDP solver
  * `tolerance::Float64 = 1e-3`
  * `verbose::Bool = true`
