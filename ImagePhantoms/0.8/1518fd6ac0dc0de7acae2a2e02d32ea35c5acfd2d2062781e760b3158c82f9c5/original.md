```
radon(ob::Object2d)::Function
```

Return function of `(r,ϕ)` that user can sample at any projection coordinates to make sinogram views of a 2D object.

The coordinate system used here is such that `ϕ=0` corresponds to line integrals along the $y$ axis for an object $f(x,y)$. Then as `ϕ` increases, the line integrals rotate counter-clockwise.
