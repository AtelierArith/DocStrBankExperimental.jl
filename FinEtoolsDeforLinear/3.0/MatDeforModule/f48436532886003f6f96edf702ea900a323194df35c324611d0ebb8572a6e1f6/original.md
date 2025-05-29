```
tens4deviator!(t::Array{T, 4}) where {T}
```

Compute 4th-order deviator tensor.

Double contraction of a second order tensor with this fourth-order tensor produces the deviator part of the second order tensor.

# Example

The product of the deviator tensor with the second-order tensor `S` is 

```
t = fill(0.0, 3, 3, 3, 3)
tens4deviator!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show tr((S - tr(S)/3*I) ), tr(tS)
```
