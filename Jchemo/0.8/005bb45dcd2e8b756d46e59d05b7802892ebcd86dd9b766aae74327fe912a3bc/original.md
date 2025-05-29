```
rmcol(X::Union{AbstractMatrix, DataFrame}, s::Union{Vector, BitVector, UnitRange, Number})
rmcol(X::Vector, s::Union{Vector, BitVector, UnitRange, Number})
```

Remove the columns of a matrix or the components of a vector  having indexes `s`.

  * `X` : Matrix or vector.
  * `s` : Vector of the indexes.

## Examples

```julia
using Jchemo

X = rand(5, 3) 
rmcol(X, [1, 3])
```
