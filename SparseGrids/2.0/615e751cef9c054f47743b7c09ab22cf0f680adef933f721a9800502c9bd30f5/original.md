```
sparsegrid( D::Int, k::Int, f::Function=gausshermite; sym::Bool=true )
```

Computation of sparse grid nodes and the associated weights

  * `D` : Dimension of integrant
  * `k` : Order of quadrature rule
  * `f` : Function generating 1D nodes and weights – in that order – for an integer input
  * `sym` : Boolean variable determining if the nodes should be symmetrized

If the nodes are supposed to be symmetric (as those in the Gauss-Hermite rule), they should be so in order to correctly identify multiply occuring nodes in the union of sparse sets
