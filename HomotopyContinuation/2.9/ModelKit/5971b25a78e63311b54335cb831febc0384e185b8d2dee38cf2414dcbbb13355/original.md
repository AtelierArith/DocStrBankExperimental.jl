```
@unique_var variable1 variable2
```

This is similar to [`@var`](@ref) with the only difference that the macro automatically changes the names of the variables to ensure uniqueness. However, the binding is still to the declared name. This is useful to ensure that there are no name collisions.

## Examples

```julia-repl
julia> @unique_var a b
(a#591, b#592)

julia> a
a#591

julia> b
b#592
```
