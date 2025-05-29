`pp = QuadraticProgram(A, b, C, d, z=zeros(..), P=I; kwargs...)`     Type for problem     `min_x 1/2xᵀPx + zᵀx, s.t Ax=b, Cx≤d`     where `P` is positive definite.

```
Keyword arguments:
`semidefinite=true` Indicates that the dual might be semidefinite, which enables iterative refinement
`ϵ = sqrt(eps(T))`  Relaxation used in iterative refinement (H+ϵI)
`smartstart=true`   Enables a smart guess on initial active set
`scaling=true`      Scales the constraints to have unit row norm

Stores: `A,b,C,d,z,P,PF,sol,boxQP` and some temporary variables.
`sol` is the solution after calling `solve!(qp)`,
`PF` is a factorization of `P`,
`boxQP::BoxConstrainedQP` representes the dual problem to be solved, with quadratic cost
`G=[A*P⁻¹*A' A*P⁻¹*C'; C*P⁻¹*A' C*P⁻¹*C']`,
linear cost `c = [A*z + b; C*z+d]`,
and constraints `0≤xᵢ ∀i>size(A,1)`.
```
