```
haveresource(T)
```

Returns `true` if `T` is an available resource. For example, `haveresource(OpenCLLibs)` tests whether the `OpenCLLibs` have been added as an available resource. This function is typically used inside a module's `__init__` function.

# Example:

```julia
# The __init__ function for MyPackage:
function __init__()
    ...  # other initialization code, possibly setting the LOAD_PATH
    if haveresource(OpenCLLibs)
        @eval using MyPackageCL  # a separate module containing OpenCL implementations
    end
    # Put additional resource checks here
    ...  # other initialization code, possibly cleaning up the LOAD_PATH
end
```
