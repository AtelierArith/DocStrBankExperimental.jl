```
to_dataframe(X::Array{T,2}; labels::Array{Symbol,1} = Symbol.("x", 1:size(X)[2]))
to_dataframe(draws::Array{Dict{Symbol,T},1}; labels::Array{Symbol,1}  = collect(keys(draws[1])))
```

Convert `Array`s or `Vector`s of `Dict`s to a `DataFrame`.
