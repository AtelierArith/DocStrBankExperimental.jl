```
label_currency(;kwargs...)
```

Convert numeric values into currency strings.

# Arguments

  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_currency()
labeler([100, 200.75]) # ["$100", "$200.75"]
```
