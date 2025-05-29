```
SDPBarrierAlg(sub_alg)
```

A meta-algorithm that handles semidefinite constraints on nonlinear functions using a barrier approach. The coefficient of the barrier term is exponentially decayed and the sub-problems are solved using `sub_alg`. `sub_alg` can be any other compatible solver from `Nonconvex.jl`. The solver must be able to solve the sub-problem after removing the semidefinite constraints. The options to the solver should be pased to the [`SDPBarrierOptions`](@ref) struct and passed in as the options to the `optimize` function. Call `? SDPBarrierOptions` to check all the different options that can be set.
