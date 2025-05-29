```
create_tensor_h1_lagrange_basis(ceed, dim, ncomp, p, q, qmode)
```

Create a tensor-product Lagrange basis.

# Arguments:

  * `ceed`:  A [`Ceed`](@ref) object where the [`Basis`](@ref) will be created.
  * `dim`:   Topological dimension of element.
  * `ncomp`: Number of field components (1 for scalar fields).
  * `p`:     Number of Gauss-Lobatto nodes in one dimension.  The polynomial degree of the          resulting $Q_k$ element is $k=p-1$.
  * `q`:     Number of quadrature points in one dimension.
  * `qmode`: Distribution of the $q$ quadrature points (affects order of accuracy for the          quadrature).
