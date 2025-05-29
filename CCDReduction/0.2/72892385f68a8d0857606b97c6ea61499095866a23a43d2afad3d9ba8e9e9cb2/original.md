```
ccds(collection)
```

Generator for `CCDData`s of entries in data frame.

Iterates over `collection` using each `path` and `hdu` to load data into a [`CCDData`](@ref).

# Examples

```julia
collection = fitscollection("~/data/tekdata")
for hdu in ccds(collection)
    @assert hdu isa CCDData
end
```
