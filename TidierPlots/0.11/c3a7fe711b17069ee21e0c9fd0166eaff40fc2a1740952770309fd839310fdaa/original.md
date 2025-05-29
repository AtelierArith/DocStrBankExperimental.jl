```
label_date(;format="m/d/Y")
```

Convert Date or DateTime values into formatted strings.

# Arguments

  * `format`: A date format string.

# Examples

```julia
labeler = label_date(format="Y-m-d")
labeler([Date(2020, 1, 1)]) # ["2020-1-1"]
```
