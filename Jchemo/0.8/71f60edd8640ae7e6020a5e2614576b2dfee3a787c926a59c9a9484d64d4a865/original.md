```
rmrow(X::Union{AbstractMatrix, DataFrame}, s::Union{Vector, BitVector, UnitRange, Number})
rmrow(X::Union{Vector, BitVector}, s::Union{Vector, BitVector, UnitRange, Number})
```

Remove the rows of a matrix or the components of a vector  having indexes `s`.

  * `X` : Matrix or vector.
  * `s` : Vector of the indexes.

## Examples

```julia
using Jchemo

X = rand(5, 2) 
rmrow(X, [1, 4])
```
