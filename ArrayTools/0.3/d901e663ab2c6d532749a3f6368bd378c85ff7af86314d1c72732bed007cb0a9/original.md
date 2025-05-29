```
bcastsize(size(A), size(B), ...) -> siz
```

yields the size `siz` of the array that would result from applying broadcasting rules (see `broadcast` method) to arguments `A`, `B`, etc. The result is a tuple of integers (of type `Int`). Call [`check_size`](@ref) if you want to also make sure that the result is a list of valid dimensions.

The method can also be applied to a single dimension:

```
bcastsize(a, b) -> c
```

to yield the dimension `c` gievn by broadcasting dimensions `a` and `b` throwing an exception if dimensions are not compatible according to broadcasting rules. This is the same as `Base.Broadcasting._bcs1` but it takes care of converting to `Int`.

See also [`standard_size`](@ref), [`check_size`](@ref), [`bcastcopy`](@ref), [`bcastlazy`](@ref).
