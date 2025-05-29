```
cpu(x)
```

Tries to move object to CPU. This works for functions, and any struct marked with `@functor`.

See also [`gpu`](@ref).

# Examples

```julia
x = x |> cpu
```
