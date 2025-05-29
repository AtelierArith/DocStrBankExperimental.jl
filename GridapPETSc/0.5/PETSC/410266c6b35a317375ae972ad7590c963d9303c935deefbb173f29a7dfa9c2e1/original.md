```
@check_error_code expr
```

Check if `expr` returns an error code equal to `zero(PetscErrorCode)`. If not, throw an instance of [`PetscError`](@ref).
