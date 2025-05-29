```
build_variable(
    _error::Function,
    info::VariableInfo,
    args...;
    kwargs...,
)
```

Return a new [`AbstractVariable`](@ref) object.

This method should only be implemented by developers creating JuMP extensions. It should never be called by users of JuMP.

## Arguments

  * `_error`: a function to call instead of `error`. `_error` annotates the error message with additional information for the user.
  * `info`: an instance of [`VariableInfo`](@ref). This has a variety of fields relating to the variable such as `info.lower_bound` and `info.binary`.
  * `args`: optional additional positional arguments for extending the [`@variable`](@ref) macro.
  * `kwargs`: optional keyword arguments for extending the [`@variable`](@ref) macro.

See also: [`@variable`](@ref)

!!! warning
    Extensions should define a method with ONE positional argument to dispatch the call to a different method. Creating an extension that relies on multiple positional arguments leads to `MethodError`s if the user passes the arguments in the wrong order.


## Examples

```julia
@variable(model, x, Foo)
```

will call

```julia
build_variable(_error::Function, info::VariableInfo, ::Type{Foo})
```

Passing special-case positional arguments such as `Bin`, `Int`, and `PSD` is okay, along with keyword arguments:

```julia
@variable(model, x, Int, Foo(), mykwarg = true)
# or
@variable(model, x, Foo(), Int, mykwarg = true)
```

will call

```julia
build_variable(_error::Function, info::VariableInfo, ::Foo; mykwarg)
```

and `info.integer` will be true.

Note that the order of the positional arguments does not matter.
