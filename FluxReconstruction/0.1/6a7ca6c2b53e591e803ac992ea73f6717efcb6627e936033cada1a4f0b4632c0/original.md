```julia
rs_jacobi(r, s, vertices)

```

Quadrilateral element

```
4       3
|-------|
|       |
|       |
|-------|
1       2
```

X = λ¹V¹ + λ²V² + λ³V³ + λ⁴V⁴

λs are bilinear rectangle shape functions:   (http://people.ucalgary.ca/~aknigh/fea/fea/rectangles/r1.html)   λ¹ = (r-1)(s-1)/4   λ² = (r+1)(1-s)/4   λ³ = (r+1)(s+1)/4   λ⁴ = (1-r)(s+1)/4

Jacobian:   Xᵣ = (s-1)V¹/4 + (1-s)V²/4 + (s+1)V³/4 - (s+1)V⁴/4   Xₛ = (r-1)V¹/4 - (r+1)V²/4 + (r+1)V³/4 + (1-r)V⁴/4

Unlike linear simplex elements, J varies from point to point within an element for a general linear quadrilateral. As a special case, the Jacobian matrix is a constant for each element in rectangular mesh.
