```
get_decorations(str::AbstractString) -> String
```

Return a string with the decorations in `str`.

# Extended Help

## Examples

```julia
julia> get_decorations("This is a \e[1mbold string\e[45mwith a different background\e[0m.")
"\e[1m\e[45m\e[0m"
```
