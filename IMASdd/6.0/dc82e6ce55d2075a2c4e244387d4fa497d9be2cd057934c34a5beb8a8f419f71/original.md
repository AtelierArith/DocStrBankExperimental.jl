```
Base.diff(
    @nospecialize(ids1::T),
    @nospecialize(ids2::T);
    tol::Float64=1E-2,
    recursive::Bool=true,
    verbose::Bool=false) where {T<:IDS}
```

Compares two IDSs and returns dictionary with differences

NOTE: This function does not evaluate expressions (use `freeze()` on the IDSs to compare values instead of functions)
