```julia
    vals = lfmm2d(eps,zk,sources;
            charges=nothing,dipstr=nothing,dipvecs=nothing,targets=nothing,pg=0,pgt=0,nd=1)
```

This subroutine computes the N-body Laplace interactions in two dimensions where the interaction kernel is given by log(r) and its gradients.

$$
    u(x) = \sum_{j=1}^{N} c_{j} * log\(\|x-x_{j}\|\) - d_{j}v_{j} \cdot \nabla( log(\|x-x_{j}\|) ),
$$

where   $c_{j}$ are the charge densities,         $d_{j}$ are the dipole strength vectors         $v_{j}$ are the dipole orientation vectors,         $x_{j}$ are the source locations. when $x=x_{j}$, the jth term is dropped from the sum

# Input

  * `eps::Float64` precision requested
  * `sources::Array{Float64}` size (2,n) source locations ($x_{j}$)

# Optional Keyword Input

  * `charges::Array{ComplexF64}` size (nd,n)
  * `dipstr::Array{ComplexF64}`  size (nd,n)
  * `dipvecs::Array{Float64}` size (nd,2,n) or (2,n) dipole orientation vectors ($d_{j}$)
  * `targets::Array{Float64}` size (2,nt) target locations ($x$)
  * `pg::Integer` source eval flag.

      * Do not compute any quantities at sources if `pg == 0`
      * Potential ($u$) at sources evaluated if `pg == 1`.
      * Potential and gradient ($\nabla u$) at sources evaluated if `pg == 2`
      * Potential, gradient, and Hessian ($\nabla \nabla u$) at sources evaluated if `pg == 3`
  * `pgt::Integer` target eval flag.

      * Do not compute any quantities at targets if `pgt == 0`
      * Potential at targets evaluated if `pgt == 1`.
      * Potential and gradient at targets evaluated if `pgt == 2`
      * Potential, gradient, and Hessian at targets evaluated if `pgt == 3`
  * `nd::Integer` number of densities

Note: if all default values are used for optional input, nothing is computed.

# Output

`vals::FMMVals` with the fields Note that the Hessian is returned as a length 4 vector at each point with the second derivatives in the order: $\partial_{xx}$, $\partial_{yy}$, $\partial_{xy}$, $\partial_{yx}$.

  * `vals.pot::Array{ComplexF64}` size (nd,n) or (n) potential at source locations if requested
  * `vals.grad::Array{ComplexF64}` size (nd,2,n) or (2,n) gradient at source locations if requested
  * `vals.hess::Array{ComplexF64}` size (nd,3,n) or (3,n) Hessian at source locations if requested
  * `vals.pottarg::Array{ComplexF64}` size (nd,nt) or (nt) potential at target locations if requested
  * `vals.gradtarg::Array{ComplexF64}` size (nd,2,nt) or (2,nt) gradient at target locations if requested
  * `vals.hesstarg::Array{ComplexF64}` size (nd,3,nt) or (3,nt) Hessian at target locations if requested
  * `vals.ier` error flag as returned by FMM2D library. A value of 0 indicates a successful call.

Non-zero values may indicate insufficient memory available. See the documentation for the FMM2D library. If not set (`nothing`), then FMM2D library was never called.
