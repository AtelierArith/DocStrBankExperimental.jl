```
jacobian(B, X, xi)
```

Given basis B, calculate jacobian at xi.

# Example

```jldoctest
B = Quad4()
X = Vec.([(0.0, 0.0), (1.0, 0.0), (1.0, 1.0), (0.0, 1.0)])
jacobian(B, X, Vec((0.0, 0.0)))

# output

2×2 Tensor{2,2,Float64,4}:
 0.5  0.0
 0.0  0.5

```
