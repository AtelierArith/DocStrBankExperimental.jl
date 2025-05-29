```
param_indices(semobj)
```

Returns a dict of parameter labels and their indices in `semobj`.

# Examples

```julia
parind = param_indices(my_fitted_sem)
parind[:param_name]
```

See also [`params`](@ref).
