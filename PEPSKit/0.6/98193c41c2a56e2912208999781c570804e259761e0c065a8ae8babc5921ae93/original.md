```
absorb_weight(t::PEPSTensor, row::Int, col::Int, ax::Int, weights::SUWeight; sqrtwt::Bool=false, invwt::Bool=false)
```

Absorb or remove environment weight on an axis of vertex tensor `t`  known to be located at position (`row`, `col`) in the unit cell. Weights around the tensor at `(row, col)` are

```
                    ↓
                [2,r,c]
                    ↓
    ← [1,r,c-1] ← T[r,c] ← [1,r,c] ←
                    ↓
                [1,r+1,c]
                    ↓
```

## Arguments

  * `t::T` : The vertex tensor to which the weight will be absorbed. The first axis of `t` should be the physical axis.
  * `row::Int` : The row index specifying the position in the tensor network.
  * `col::Int` : The column index specifying the position in the tensor network.
  * `ax::Int` : The axis into which the weight is absorbed, taking values from 1 to 4, standing for north, east, south, west respectively.
  * `weights::SUWeight` : The weight object to absorb into the tensor.

## Keyword arguments

  * `sqrtwt::Bool=false` : If `true`, the square root of the weight is absorbed.
  * `invwt::Bool=false` : If `true`, the inverse of the weight is absorbed.

## Examples

```julia
# Absorb the weight into the north axis of tensor at position (2, 3)
absorb_weight(t, 2, 3, 1, weights)

# Absorb the square root of the weight into the south axis
absorb_weight(t, 2, 3, 3, weights; sqrtwt=true)

# Absorb the inverse of (i.e. remove) the weight into the east axis
absorb_weight(t, 2, 3, 2, weights; invwt=true)
```
