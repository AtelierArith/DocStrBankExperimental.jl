```
value_flatten([eltype=Float64], x)
```

Operates similarly to `flatten`, but the returned `unflatten` function returns an object like `x`, but with unwrapped values.

Doing

```julia
v, unflatten = value_flatten(x)
```

is the same as doing

```julia
v, _unflatten = flatten(x)
unflatten = ParameterHandling.value ∘ _unflatten
```
