```
instantiate(granules::Vector{::Granule}, folder::AbstractString)
```

For a given list of `granules` from [`find`](@ref), match the granules to the local files and return a new list of granules with the local filepaths if they exist.
