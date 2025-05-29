```
grid(P, n...)
```

Creates a grid of points. if `n` is unspecified it will be sufficient number of points to determine `size(P,2)` coefficients. If `n` is an integer or `Block` its enough points to determine `n` coefficients. If `n` is a tuple then it returns a tuple of grids corresponding to a tensor-product. That is, a 5⨱6 2D transform would be

```julia
(x,y) = grid(P, (5,6))
plan_transform(P, (5,6)) * f.(x, y')
```

and a 5×6×7 3D transform would be

```julia
(x,y,z) = grid(P, (5,6,7))
plan_transform(P, (5,6,7)) * f.(x, y', reshape(z,1,1,:))
```
