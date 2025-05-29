```
(launcher::Launcher)(arch::Architecture, grid, kernel_and_args::Pair{F,Args}; bc=nothing) where {F,Args}
```

Launches a computational kernel using the specified `arch`, `grid`, `kernel_and_args`, and optional boundary conditions (`bc`).

## Arguments:

  * `arch::Architecture`: The architecture on which to execute the computation.
  * `grid`: The grid defining the computational domain.
  * `kernel_and_args::Pair{F,Args}`: A pair consisting of the computational kernel `F` and its arguments `Args`.
  * `bc=nothing`: Optional boundary conditions for the computation.

!!! warning
      * `arch` should be compatible with the `Launcher`'s architecture.
      * If `bc` is `nothing`, the kernel is launched without boundary conditions.
      * The function waits for the computation to complete before returning.

