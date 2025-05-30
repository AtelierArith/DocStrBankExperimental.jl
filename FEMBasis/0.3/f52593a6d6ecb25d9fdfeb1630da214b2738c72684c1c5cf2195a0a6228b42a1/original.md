```
grad(B, T, X, xi)
```

Calculate gradient of `T` with respect to `X` in point `xi` using basis `B`.

# Example

```jldoctest
B = Quad4()
X = Vec.([(0.0, 0.0), (1.0, 0.0), (1.0, 1.0), (0.0, 1.0)])
u = Vec.([(0.0, 0.0), (1.0, -1.0), (2.0, 3.0), (0.0, 0.0)])
grad(B, u, X, Vec(0.0, 0.0))

# output

julia> grad(B, u, X, Vec(0.0, 0.0))
2×2 Tensor{2,2,Float64,4}:
 1.5  0.5
 1.0  2.0

```
