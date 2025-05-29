```julia
MultiSelect(options::Vector; [default], [size::Int])
# or with a custom display value:
MultiSelect(options::Vector{Pair{Any,String}}; [default], [size::Int])
```

A multi-selector - the user can choose one or more of the `options`.

See [`Select`](@ref) for a version that allows only one selected item.

# Examples

```julia
@bind vegetables MultiSelect(["potato", "carrot"])

if "carrot" ∈ vegetables
	"yum yum!"
end
```

```julia
@bind chosen_functions MultiSelect([sin, cos, tan, sqrt])

[f(0.5) for f in chosen_functions]
```

You can also specify a display value by giving pairs `bound_value => display_value`:

```julia
@bind chosen_functions MultiSelect([
	cos => "cosine function", 
	sin => "sine function",
])

[f(0.5) for f in chosen_functions]
```

The `size` keyword argument may be used to specify how many rows should be visible at once.

```julia
@bind letters MultiSelect(string.('a':'z'), size=20)
```
