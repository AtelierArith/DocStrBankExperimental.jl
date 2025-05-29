```
ftcall(f::Function, ft::FrankenTuple)
```

Call the function `f` using the unnamed portion of `ft` as its positional arguments and the named portion of `ft` as its keyword arguments.

# Examples

```jldoctest
julia> ftcall(mapreduce, ftuple(abs2, -, 1:4; init=0))
-30
```
