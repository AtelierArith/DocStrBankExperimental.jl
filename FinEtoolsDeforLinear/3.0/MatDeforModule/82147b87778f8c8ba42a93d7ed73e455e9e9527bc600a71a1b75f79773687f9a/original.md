```
tens4identity!(t::Array{T, 4}) where {T}
```

Compute 4th-order identity tensor.

# Example

The product of the identity tensor with the second-order tensor `S` is 

```
t = fill(0.0, 3, 3, 3, 3)
tens4identity!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show S - tS
```
