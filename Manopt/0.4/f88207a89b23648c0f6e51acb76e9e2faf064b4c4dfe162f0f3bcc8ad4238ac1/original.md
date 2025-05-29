```
CoordinateVectorialType{B<:AbstractBasis} <: AbstractVectorialType
```

A type to indicate that gradient of the constraints is implemented as a Jacobian matrix with respect to a certain basis, that is if the constraints are given as $g: \mathcal M → ℝ^m$ with respect to a basis $\mathcal B$ of $T_p\mathcal M$, at $p∈ \mathcal M$ This can be written as $J_g(p) = (c_1^{\mathrm{T}},…,c_m^{\mathrm{T}})^{\mathrm{T}} \in ℝ^{m,d}$, that is, every row $c_i$ of this matrix is a set of coefficients such that `get_coefficients(M, p, c, B)` is the tangent vector $\oepratorname{grad} g_i(p)$

for example $g_i(p) ∈ ℝ^m$ or $\operatorname{grad} g_i(p) ∈ T_p\mathcal M$,     $i=1,…,m$.

# Fields

  * `basis` an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) to indicate the default representation.
