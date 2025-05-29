```
label_percent(;kwargs...)
```

Convert numeric values into percentage strings.

# Arguments

  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_percent()
labeler([0.1, 0.256]) # ["10%", "25.6%"]
```
