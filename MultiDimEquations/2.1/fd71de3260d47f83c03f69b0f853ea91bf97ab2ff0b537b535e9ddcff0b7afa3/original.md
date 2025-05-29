```
toDataFrame(idxtable::NDSparse)
```

Convert a single-value-column NDSParse table to `DataFrame`.

# Arguments

  * `idxtable`: The NDSParse table to convert

# Examples

```julia
julia> content = [["banana","banana","apple","apple","orange"],["us",missing,"us","eu","us"],[1.1,2.2,3.3,missing,5.5]]
julia> dimNames = ["item","region"]
julia> t = NDSparse(content...,names=Symbol.(dimNames))
julia> df = toDataFrame(t)
```
