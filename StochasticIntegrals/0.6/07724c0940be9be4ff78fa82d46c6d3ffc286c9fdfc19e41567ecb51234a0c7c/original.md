```
to_draws(X::Array{T,2}; labels::Array{Symbol,1} = Symbol.("x", 1:size(X)[2]))
to_draws(dd::DataFrame; labels::Array{Symbol,1} =  Symbol.(names(dd)))
```

Convert array or dataframe to a vector of `Dict`s containing draws.
