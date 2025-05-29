```
get_hessian(M::AbstractManifold, vgf::VectorHessianFunction, p, X, i)
get_hessian(M::AbstractManifold, vgf::VectorHessianFunction, p, X, i, range)
get_hessian!(M::AbstractManifold, X, vgf::VectorHessianFunction, p, X, i)
get_hessian!(M::AbstractManifold, X, vgf::VectorHessianFunction, p, X, i, range)
```

Evaluate the Hessians of the vector function `vgf` on the manifold `M` at `p` in direction `X` and the values given in `range`, specifying the representation of the gradients.

Since `i` is assumed to be a linear index, you can provide

  * a single integer
  * a `UnitRange` to specify a range to be returned like `1:3`
  * a `BitVector` specifying a selection
  * a `AbstractVector{<:Integer}` to specify indices
  * `:` to return the vector of all gradients
