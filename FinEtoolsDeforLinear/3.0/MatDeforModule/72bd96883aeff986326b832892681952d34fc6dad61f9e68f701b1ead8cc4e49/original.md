```
tens4tracor!(t::Array{T, 4}) where {T}
```

Compute 4th-order tracor tensor.

Double contraction of a second order tensor with this fourth-order tensor produces the spherical part of the second order tensor.

# Example

The product of the tracor tensor with the second-order tensor `S` is 

```
t = fill(0.0, 3, 3, 3, 3)
tens4tracor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show tr(S) * I - tS
```
