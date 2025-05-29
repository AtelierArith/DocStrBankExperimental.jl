```
r = random_rotation_matrix() # rotation matrix in cartesian coords
```

Generate a 3x3 random rotation matrix `r` such that when a point `x` is rotated using this rotation matrix via `r * x`, this point `x` is placed at a uniform random distributed position on the surface of a sphere of radius `norm(x)`. the point `x` is in Cartesian coordinates here. See James Arvo. Fast Random Rotation Matrices.

https://pdfs.semanticscholar.org/04f3/beeee1ce89b9adf17a6fabde1221a328dbad.pdf

# Returns

  * `r::Array{Float64, 2}`: A 3x3 random rotation matrix
