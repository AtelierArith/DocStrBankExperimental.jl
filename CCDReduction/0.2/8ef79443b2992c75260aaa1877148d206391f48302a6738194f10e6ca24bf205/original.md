```
arrays(collection)
```

Generator for arrays of images of entries in data frame.

Iterates over `collection` using each `path` and `hdu` to load data into an `Array`.

# Examples

```julia
collection = fitscollection("~/data/tekdata")
data = arrays(collection) |> collect
```

This returns all image arrays present in `collection`. This can also be used via a for-loop

```julia
collection = fitscollection("~/data/tekdata")
for arr in arrays(collection)
    @assert arr isa Array
    println(size(arr))
end

# output
(1048, 1068)
(1048, 1068)
...
```
