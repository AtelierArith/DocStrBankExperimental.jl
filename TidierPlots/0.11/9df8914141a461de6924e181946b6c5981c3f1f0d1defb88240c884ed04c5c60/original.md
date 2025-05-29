```
label_ordinal(;kwargs...)
```

Convert numeric values into ordinal strings (e.g., 1st, 2nd, 3rd).

# Arguments

  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_ordinal()
labeler([1, 2, 3]) # ["1st", "2nd", "3rd"]
```
