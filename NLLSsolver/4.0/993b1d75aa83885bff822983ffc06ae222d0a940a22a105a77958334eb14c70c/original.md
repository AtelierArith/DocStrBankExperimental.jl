```
update(oldvar, updatevec, start::Int=1)
```

Update `oldvar` using the `nvars(oldvar)` values in `updatevec::AbstractVector`, starting at  element `start`, and return the new value. 

The update input `updatevec` may have an autodiff element type, so the variable type and this method must support a change in internal element datatype.

Default implementations of this method exist for types `Number`, `Vector` and  `StaticVector`.

# Example

The `update` function for the `Number` abstract type is:

```julia
    NLLSsolver.update(var::Number, updatevec, start=1) = var + updatevec[start]
```

!!! note
    Required user-specialized API function.

