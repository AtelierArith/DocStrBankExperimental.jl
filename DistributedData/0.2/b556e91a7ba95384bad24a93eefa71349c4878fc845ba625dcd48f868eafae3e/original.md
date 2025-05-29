```
dstat(dInfo::Dinfo, columns::Vector{Int})::Tuple{Vector{Float64}, Vector{Float64}}
```

Compute mean and standard deviation of the columns in dataset. Returns a tuple with a vector of means in `columns`, and a vector of corresponding sdevs.
