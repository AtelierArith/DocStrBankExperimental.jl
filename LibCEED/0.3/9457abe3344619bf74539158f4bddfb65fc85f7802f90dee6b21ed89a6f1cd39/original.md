```
create_h1_basis(c::Ceed, topo::Topology, ncomp, nnodes, nqpts, interp, grad, qref, qweight)
```

Create a non tensor-product basis for $H^1$ discretizations

# Arguments:

  * `ceed`:    A [`Ceed`](@ref) object where the [`Basis`](@ref) will be created.
  * `topo`:    [`Topology`](@ref) of element, e.g. hypercube, simplex, etc.
  * `ncomp`:   Number of field components (1 for scalar fields).
  * `nnodes`:  Total number of nodes.
  * `nqpts`:   Total number of quadrature points.
  * `interp`:  Matrix of size `(nqpts, nnodes)` expressing the values of nodal basis functions            at quadrature points.
  * `grad`:    Array of size `(dim, nqpts, nnodes)` expressing derivatives of nodal basis            functions at quadrature points.
  * `qref`:    Matrix of size `(dim, nqpts)` holding the locations of quadrature points on the            reference element $[-1, 1]$.
  * `qweight`: Array of length `nqpts` holding the quadrature weights on the reference            element.
