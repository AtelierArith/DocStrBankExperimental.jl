```
BoundedCylinder(radius::T, height::T; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

Create a cylinder with planar caps on both ends centered at `(0, 0, 0)` with axis `(0, 0, 1)`.
