```
grad(B, X, xi)
```

Given basis B, calculate gradient dB/dX at xi.

# Example

```jldoctest
B = Quad4()
X = Vec.([(0.0, 0.0), (1.0, 0.0), (1.0, 1.0), (0.0, 1.0)])
grad(B, X, Vec(0.0, 0.0))

# output

4-element Array{Tensor{1,2,Float64,2},1}:
 [-0.5, -0.5]
 [0.5, -0.5]
 [0.5, 0.5]
 [-0.5, 0.5]

```
