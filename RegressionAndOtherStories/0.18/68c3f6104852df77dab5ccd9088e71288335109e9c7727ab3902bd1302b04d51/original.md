# scale!

Augment a DataFrame with scaled values of 1 or more columns

### Method

```julia
scale!(df, var, ext) 
```

### Required arguments

```julia
* `df::DataFrame`                      : DataFrame
* `var::Union{Symbol, Vector{Symbol}}` : Variables to scale
* `ext::String="_s"`                   : Suffix for scaled variable(s)
```

### Return values

```julia
* `result::DataFrame`                  : Augmented DataFrame
```

### Example

```julia
scale!(df, :var1)

or

scale!(mydf, [:var1, var2])
```
