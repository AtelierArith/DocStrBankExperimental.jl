```julia
Select(options::Vector; [default])
# or with a custom display value:
Select(options::Vector{Pair{Any,String}}; [default::Any])
```

A dropdown menu - the user can choose an element of the `options` vector.

See [`MultiSelect`](@ref) for a version that allows multiple selected items.

# Examples

```julia
@bind veg Select(["potato", "carrot"])
```

```julia
@bind f Select([sin, cos, tan, sqrt])

f(0.5)
```

You can also specify a display value by giving pairs `bound_value => display_value`:

```julia
@bind f Select([cos => "cosine function", sin => "sine function"])

f(0.5)
```
