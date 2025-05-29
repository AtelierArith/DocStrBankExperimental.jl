```
PETScSNES(; petsclib = missing, autodiff = nothing, mpi_comm = missing, kwargs...)
```

Wrapper over [PETSc.jl](https://github.com/JuliaParallel/PETSc.jl) SNES solvers.

### Keyword Arguments

  * `petsclib`: PETSc library to use. If set to `missing`, then we will use the first available PETSc library in `PETSc.petsclibs` based on the problem element type.
  * `autodiff`: the choice of method for generating the Jacobian. Defaults to `nothing` which means that a default is selected according to the problem specification. Can be any valid ADTypes.jl autodiff type (conditional on that backend being supported in NonlinearSolve.jl). If set to `missing`, then PETSc computes the Jacobian using finite differences.
  * `mpi_comm`: MPI communicator to use. If set to `missing`, then we will use `MPI.COMM_SELF`.
  * `kwargs`: Keyword arguments to be passed to the PETSc SNES solver. See [PETSc SNES documentation](https://petsc.org/release/manual/snes/) and [SNESSetFromOptions](https://petsc.org/release/manualpages/SNES/SNESSetFromOptions) for more information.

### Options via `CommonSolve.solve`

These options are forwarded from `solve` to the PETSc SNES solver. If these are provided to `kwargs`, then they will be ignored.

| `solve` option | PETSc SNES option |
|:-------------- |:----------------- |
| `atol`         | `snes_atol`       |
| `rtol`         | `snes_rtol`       |
| `maxiters`     | `snes_max_it`     |
| `show_trace`   | `snes_monitor`    |

!!! note
    This algorithm is only available if `PETSc.jl` is installed and loaded.

