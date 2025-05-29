```
Dictionary(inds, values)
Dictionary{I}(inds, values)
Dictionary{I, T}(inds, values)
```

Construct a hash-based dictionary from two iterable inputs `inds` and `values`. The first value of `inds` will be the index for the first value of `values`. The input might not be copied.

Note: the values of `inds` must be distinct. Consider using `dictionary(zip(inds, values))` if they are not. See also the `index` function.

# Example

julia> Dictionary(["a", "b", "c"], [1, 2, 3]) 3-element Dictionary{String,Int64}  "a" │ 1  "b" │ 2  "c" │ 3

julia> Dictionary{String, Float64}(["a", "b", "c"], [1, 2, 3]) 3-element Dictionary{String,Float6464}  "a" │ 1.0  "b" │ 2.0  "c" │ 3.0
