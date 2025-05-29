```
filenames(collection)
```

Generator for filenames of entries in data frame.

Iterates over `collection` using each `path`.

# Examples

```julia
collection = fitscollection("~/data/tekdata")
for path in filenames(collection)
    @assert path isa String
    println(path)
end

# output
"~/data/tekdata/tek001.fits"
"~/data/tekdata/tek002.fits"
...
```
