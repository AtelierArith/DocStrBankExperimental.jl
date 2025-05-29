```julia
    function load(filename::String)
```

Load and retur an `object` stored to a file,  which full path is given as `filemane`.

It can be used, for instance, to load [`CVres`](@ref) structures and [`Pipeline`](@ref) tuples.

For pipelines, there is no check that it matches the dimension of the data  to which it will be applied. This is the user's responsibility.

**See** [`saveas`](@ref)
