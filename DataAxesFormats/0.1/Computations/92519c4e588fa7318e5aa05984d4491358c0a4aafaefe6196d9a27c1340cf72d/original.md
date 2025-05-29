When using [`@computation`](@ref):

```
'''
...
# Contract
...
$(CONTRACT)
...
'''
@computation Contract(...) function something(daf::DafWriter, ...)
    return ...
end
```

Then `$(CONTRACT)` will be expanded with a description of the [`Contract`](@ref). This is based on `DocStringExtensions`.

!!! note
    The first argument of the function must be a [`DafWriter`](@ref), which the contract will be applied to.

