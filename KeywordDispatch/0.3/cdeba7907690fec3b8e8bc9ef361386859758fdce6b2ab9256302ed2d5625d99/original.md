```
@kwmethod expr
```

Define a keyword method for dispatch. `expr` should be a standard function definition (either block or inline) with a keyword argument block (which may be empty).

The positional signature should first be designated by the [`@kwdispatch`](@ref) macro.

# Examples

```julia
@kwdispatch f() # designate the no positional argument form

@kwmethod f(;) = nothing # no keyword arguments
@kwmethod f(;a) = a
@kwmethod f(;b) = 2*b
@kwmethod f(;a,b) = a+2*b
```
