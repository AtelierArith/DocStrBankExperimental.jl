```
uniform_mesh(elem::Line,Kx)
uniform_mesh(elem::Tri,Kx,Ky)
uniform_mesh(elem::Quad,Kx,Ky)
uniform_mesh(elem::Hex,Kx,Ky,Kz)
uniform_mesh(elem, K)
```

Uniform `Kx` (by `Ky` by `Kz`) mesh on $[-1,1]^d$, where `d` is the spatial dimension. Returns `(VX,VY,VZ)`, `EToV`. When only one `K` is specified, it assumes a uniform mesh with `K` elements in each coordinate direction.

`K` can also be specified using a keyword argument `K1D`, e.g., `uniform_mesh(elem; K1D = 16)`.
