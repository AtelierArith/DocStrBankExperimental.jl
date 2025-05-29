```
GTNSolver(; optimizer=TreeSA(), single=false, usecuda=false, T=Float64)
```

A generic tensor network based backend for the `findbest`, `findmin` and `findmax` interfaces in `ProblemReductions.jl`.

## Keyword arguments

  * `optimizer` is the optimizer for the tensor network contraction.
  * `single` is a switch to return single solution instead of all solutions.
  * `usecuda` is a switch to use CUDA (when applicable), user need to call statement `using CUDA` before turning on this switch.
  * `T` is the "base" element type, sometimes can be used to reduce the memory cost.
