```
download!(granules::Vector{<:Granule}, folder=".")
```

Like [`download!`](@ref), but for a vector of `granules`. Will make use of aria2c (parallel).
