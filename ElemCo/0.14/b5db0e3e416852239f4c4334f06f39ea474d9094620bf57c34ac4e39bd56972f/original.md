```
@set(opt, kwargs...)
```

Set options for `EC::ECInfo`. 

The first argument `opt` is the name of the option (e.g., `scf`, `cc`, `cholesky`), see [`ECInfos.Options`](@ref).   The keyword arguments are the options to be set (e.g., `thr=1.e-14`, `maxit=10`).   The current state of the options can be stored in a variable, e.g., `opt_cc = @set cc`.   The state can then be restored by `@set cc opt_cc`.   If `EC` is not already initialized, it will be done. 

# Examples

```julia
optscf = @set scf thr=1.e-14 maxit=10
@set cc maxit=100
...
@set scf optscf
```
