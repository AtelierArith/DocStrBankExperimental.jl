```
@path expr [ignore]
```

Define a "relocatable" path. Its contents will be available regardless of whether the original path still exists or not. The contents of the path is stored within the returned `Path` object and the folder structure is recreated as a scratchspace if the original does not exist anymore. Calling any path manipulation functions, such as `joinpath`, on the `Path` will return a path to a valid folder.

`ignore` can be used to skip reading in matching files. It can be a `Regex`, `Vector{Regex}`, or a single argument `Function` that takes the path and returns `true` if it should be ignored, `false` otherwise.
