```
to_array(draws::Array{Dict{Symbol,T},1}; labels::Array{Symbol,1}  = collect(keys(draws[1]))) where T<:Real
to_array(dd::DataFrame; labels::Array{Symbol,1} =  Symbol.(names(dd)))
```

Convert draws or a `DataFrame` to an array and a vector of column labels.
