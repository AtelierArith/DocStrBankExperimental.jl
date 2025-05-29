```
get_jacobian(M::AbstractManifold, vgf::AbstractVectorGradientFunction, p; kwargs...)
get_jacobian(M::AbstractManifold, J, vgf::AbstractVectorGradientFunction, p; kwargs...)
```

Compute the Jacobian $J_F ∈ ℝ^{m×n}$ of the [`AbstractVectorGradientFunction`](@ref) $F$ at `p` on the `M`.

There are two interpretations of the Jacobian of a vectorial function $F: \mathcal M → ℝ^m$ on a manifold. Both depend on choosing a basis on the tangent space $T_{p}\mathcal M$ which we denote by $Y_1,…,Y_n$, where `n` is the [`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)``(M)`. We can write any tangent vector $X = \displaystyle\sum_i c_iY_i$

1. The Jacobian $J_F$ is the matrix with respect to the basis $Y_1,…,Y_n$ such that

for any $X∈T_{p}\mathcal M$ we have the equality of the differential $DF(p)[X] = Jc$.   In other words, the `j`th column of $J$ is given by $DF(p)[Y_j]$

2. Given the gradients $\operatorname{grad} F_i(p)$ of the component functions $F_i: \mathcal M → ℝ$,

we define the jacobian function as

$math   J(X) = \begin{pmatrix} ⟨\operatorname{grad} F_1, X⟩_p\\ ⟨\operatorname{grad} F_1, X⟩_p\\ ⋮\\ ⟨\operatorname{grad} F_1, X⟩_p\end{pmatrix}$

Then either the $j$th column of $J_F$ is given by $J(Y_i)$ or the $i$th row is given by all inner products $\operatorname{grad} F_1, Y_j⟩_p$ of the $i$th gradient function with all basis vectors $Y_j$.

The computation can be computed in-place of `J`.

# Keyword arguments

  * `basis::AbstractBasis =`[`get_basis`](@ref)`(vgf)` for the [`CoordinateVectorialType`](@ref) of the vectorial functions gradient, this might lead to a change of basis, if this basis and the one the coordinates are given in do not agree.
  * `range::AbstractPowerRepresentation =`[`get_range`](@ref)`(vgf.jacobian_type)` specify the range of the gradients in the case of a [`FunctionVectorialType`](@ref), that is, on which type of power manifold the gradient is given on.
