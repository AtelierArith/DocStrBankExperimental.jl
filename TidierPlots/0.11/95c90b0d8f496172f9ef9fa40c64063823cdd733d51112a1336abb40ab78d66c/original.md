```
label_scientific(;kwargs...)
```

Convert numeric values into scientific notation strings.

# Arguments

  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_scientific()
labeler([1000, 2000000]) # ["1e+03", "2e+06"]
```
