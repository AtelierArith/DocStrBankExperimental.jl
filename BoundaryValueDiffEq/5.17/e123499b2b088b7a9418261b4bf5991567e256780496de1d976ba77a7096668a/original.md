```
BVPM2(; max_num_subintervals = 3000, method_choice = 4, diagnostic_output = 1,
    error_control = 1, singular_term = nothing)
BVPM2(max_num_subintervals::Int, method_choice::Int, diagnostic_output::Int,
    error_control::Int, singular_term)
```

Fortran code for solving two-point boundary value problems. For detailed documentation, see [ODEInterface.jl](https://github.com/luchr/ODEInterface.jl/blob/master/doc/SolverOptions.md#bvpm2).

## Keyword Arguments:

```
- `max_num_subintervals`: Number of maximal subintervals, default as 3000.
- `method_choice`: Choice for IVP-solvers, default as Runge-Kutta method of order 4,
  available choices:
    - `2`: Runge-Kutta method of order 2.
    - `4`: Runge-Kutta method of order 4.
    - `6`: Runge-Kutta method of order 6.
- `diagnostic_output`: Diagnostic output for BVPM2, default as non printout, available
  choices:
    - `-1`: Full diagnostic printout.
    - `0`: Selected printout.
    - `1`: No printout.
- `error_control`: Determines the error-estimation for which RTOL is used, default as
  defect control, available choices:
    - `1`: Defect control.
    - `2`: Global error control.
    - `3`: Defect and then global error control.
    - `4`: Linear combination of defect and global error control.
- `singular_term`: either nothing if the ODEs have no singular terms at the left
  boundary or a constant (d,d) matrix for the
    singular term.
```

!!! note
    Only available if the `ODEInterface` package is loaded.

