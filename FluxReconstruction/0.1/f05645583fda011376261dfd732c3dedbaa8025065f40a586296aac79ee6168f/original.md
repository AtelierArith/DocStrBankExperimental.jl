```julia
rs_jacobi(cells, points)

```

Calculate Jacobians for elements

Isosceles right triangle element

```
3
|
|  
|
|-------|
1       2
```

X = [x, y] = λ¹V¹ + λ²V² + λ³V³

λs are linear:   λ¹ = -(r+s)/2   λ² = (r+1)/2 λ³ = (s+1)/2

Jacobian:   [xr xs    yr ys]

Xᵣ = -V¹/2 + V²/2   Xₛ = -V¹/2 + V³/2
