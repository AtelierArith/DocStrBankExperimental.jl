```
SerializedElementArrays.disk(array::AbstractArray; cleanup=true, path=tempdir())
```

Convert the `AbstractArray` `array` to an array saved on disk of type `SerializedElementArrays.SerializedElementArray`. Each element of the array will be saved in serialized format to an individual file in a randomly generated directory.

If an `array` of type `SerializedElementArray` is input, this will simply return the original `array` (it acts like a conversion to type `SerializedElementArray`), ignoring the keyword arguments.

# Arguments

  * `array::AbstractArray`: the array to convert to a `SerializedElementArrays.SerializedElementArray` stored on disk.

# Keywords

  * `cleanup::Bool=true`: controls whether the process attempts to delete the returned path automatically when the process exits.
  * `path=tempdir()`: the root of the path where a temporary directory will be made where the elements of the array will be saved. A directory with a random name assigned by the Base function `tempname` will be used.

!!! compat "Julia 1.4"
    This makes use of the Julia function `tempname` to create a temporary directory where the elements of the array will be saved. `tempname` only supports customizing the path and automatically cleaning up the files in Julia 1.4 and later. The `path` and `cleanup` arguments are only supported in Julia 1.4 and later, and in those previous versions they will default to `cleanup=false` and `path=tempdir()`.

