```
tens4skewor!(t::Array{T, 4}) where {T}
```

Compute 4th-order skewor tensor.

Double contraction of a second order tensor with this fourth-order tensor produces the skew part of the second order tensor.

# Example

The product of the skewor tensor with the second-order tensor `S` is 

```
t = fill(0.0, 3, 3, 3, 3)
tens4skewor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show (S - S')/2 * I - tS
```
