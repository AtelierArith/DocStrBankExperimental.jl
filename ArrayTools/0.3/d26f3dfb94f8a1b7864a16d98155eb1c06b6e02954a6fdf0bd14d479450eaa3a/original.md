```
all_indices(A...)
```

yields an iterable object for visiting each index of array(s) `A` in an efficient manner. For array types that have opted into fast linear indexing (like `Array`), this is simply the range `1:length(A)`. For other array types, return a specialized Cartesian range to efficiently index into the array(s) with indices specified for every dimension.

If more than one `AbstractArray` argument are supplied, `all_indices` will create an iterable object that is fast for all arguments (a `UnitRange` if all inputs have fast linear indexing, a `CartesianIndices` otherwise). A `DimensionMismatch` exception is thrown if the arrays have different axes so that it is always safe to use `@inbounds` in front of a loop like:

for i in all_indices(A, B, C, D)        A[i] = B[i]*C[i] + D[i]    end

when `A`, `B` etc. are all (abstract) arrays.

This method is similar to `eachindex` except that a `DimensionMismatch` exception is thrown if arrays have different axes. For linearly indexed arrays, `eachindex` only checks that they have the same linear index range (that is the same number of elements, not the same shape).
