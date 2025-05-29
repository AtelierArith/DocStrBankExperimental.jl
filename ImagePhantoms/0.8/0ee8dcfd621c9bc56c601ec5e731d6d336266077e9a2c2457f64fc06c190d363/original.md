```
radon(ob::Object3d)::Function
```

Return function of `(u,v,ϕ,θ)` that user can sample at any projection coordinates to make projection views of a 3D object.

The coordinate system used here is such that `ϕ=0` corresponds to line integrals along the $y$ axis for an object $f(x,y,z)$. Then as `ϕ` increases, the line integrals rotate counter-clockwise.
