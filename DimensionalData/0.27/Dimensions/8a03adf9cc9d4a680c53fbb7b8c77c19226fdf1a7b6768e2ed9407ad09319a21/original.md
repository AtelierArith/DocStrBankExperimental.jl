```
setdims(X, newdims) => AbstractArray
setdims(::Tuple, newdims) => Tuple{Vararg{Dimension,N}}
```

Replaces the first dim matching `<: basetypeof(newdim)` with newdim, and returns a new object or tuple with the dimension updated.

## Arguments

  * `x`: any object with a `dims` method, a `Tuple` of `Dimension` or a single `Dimension`.
  * `newdim`: Tuple or single `Dimension`, `Type` or `Symbol`.

# Example

```jldoctest
using DimensionalData, DimensionalData.Dimensions, DimensionalData.Lookups
A = ones(X(10), Y(10:10:100))
B = setdims(A, Y(Categorical('a':'j'; order=ForwardOrdered())))
lookup(B, Y)
# output
Categorical{Char} ForwardOrdered
wrapping: 'a':1:'j'
```
