```julia
ReverseDiffVJP{compile} <: VJPChoice
```

Uses ReverseDiff.jl to compute the vector-Jacobian products. If `f` is in-place, then it uses a array of structs formulation to do scalarized reverse mode, while if `f` is out-of-place, then it uses an array-based reverse mode.

Usually, the fastest when scalarized operations exist in the f function (like in scientific machine learning applications like Universal Differential Equations) and the boolean compilation is enabled (i.e. ReverseDiffVJP(true)), if EnzymeVJP fails on a given choice of `f`.

Does not support GPUs (CuArrays).

## Constructor

```julia
ReverseDiffVJP(compile = false)
```

## Keyword Arguments

  * `compile`: Whether to cache the compilation of the reverse tape. This heavily increases the performance of the method, but requires that the `f` function of the ODE/DAE/SDE/DDE has no branching.
