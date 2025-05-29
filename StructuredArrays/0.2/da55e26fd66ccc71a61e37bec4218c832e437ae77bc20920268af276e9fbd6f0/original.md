```
StructuredArray([S = IndexCartesian,] func, args...) -> A
StructuredArray{T}([S = IndexCartesian,] func, args...) -> A
StructuredArray{T,N}([S = IndexCartesian,] func, args...) -> A
StructuredArray{T,N,S}(func, args...) -> A
```

build a `N`-dimensional array `A` whose values at index `i` are computed as `func(i)` and whose shape is specified by `args...`. The storage requirement is `O(1)` instead of `O(lenght(A))` for an ordinary array. Optional parameters `T`, `N`, and `S` are to specify the element type, the number of dimensions, and the type of the indexing style of the array. If specified as an argument, not as a type parameter, `S` may also be an instance of `IndexStyle`.

The function `func` is called with the index specified as in base method `getindex`: if indexing style is `IndexCartesian` (the default), the function `func` will be called with `N` integer arguments (a `Vararg{Int,N}`); if `S` is `IndexLinear`, the function `func` will be called with a single integer argument (an `Int`).

For example, the structure of a lower triangular matrix of size `m×n` could be given by:

```
StructuredArray((i,j) -> (i ≥ j), m, n)
```

but with a constant small storage requirement whatever the size of the matrix.

Although the callable object `func` may not be a *pure function*, its return type shall be stable and structured arrays are considered as immutable in the sense that a statement like `A[i] = x` is not implemented. If parameter `T` is not specified in the call to the constructor, the type of the elements of structured array is inferred by applying `func` to the unit index.
