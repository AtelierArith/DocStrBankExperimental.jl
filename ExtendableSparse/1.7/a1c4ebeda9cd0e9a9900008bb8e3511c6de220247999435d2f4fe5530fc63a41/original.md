```julia
sprand_sdd!(A; nnzrow)

```

Fill sparse matrix  with random entries such that  it becomes strictly diagonally  dominant  and  thus  invertible and  has  a  fixed  number `nnzrow` (default: 4) of nonzeros in its rows. The matrix bandwidth is bounded by  sqrt(n) in order to resemble  a typical matrix of  a 2D piecewise linear FEM discretization.
