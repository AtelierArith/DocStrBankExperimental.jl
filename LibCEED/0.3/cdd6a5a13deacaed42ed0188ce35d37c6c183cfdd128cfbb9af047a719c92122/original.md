```
create_tensor_h1_basis(c::Ceed, dim, ncomp, p, q, interp1d, grad1d, qref1d, qweight1d)
```

Create a tensor-product basis for $H^1$ discretizations.

# Arguments:

  * `ceed`:      A [`Ceed`](@ref) object where the [`Basis`](@ref) will be created.
  * `dim`:       Topological dimension.
  * `ncomp`:     Number of field components (1 for scalar fields).
  * `p`:         Number of nodes in one dimension.
  * `q`:         Number of quadrature points in one dimension
  * `interp1d`:  Matrix of size `(q, p)` expressing the values of nodal basis functions at              quadrature points.
  * `grad1d`:    Matrix of size `(p, q)` expressing derivatives of nodal basis functions at              quadrature points.
  * `qref1d`:    Array of length `q` holding the locations of quadrature points on the 1D              reference element $[-1, 1]$.
  * `qweight1d`: Array of length `q` holding the quadrature weights on the reference element.
