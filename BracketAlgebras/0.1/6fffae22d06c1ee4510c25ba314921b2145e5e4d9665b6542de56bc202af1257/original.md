```
BracketAlgebra{T<:RingElement} <: AbstractBracketAlgebra{T}
```

Bracket algebra with coefficients of type `T`.

# Fields

  * `d::Int`: dimension of the underlying projective space P^`d`
  * `n::Int`: number of points considered
  * `R::MPolyRing{T}`: AbstractAlgebra multivariate polynomial ring representing the elements of the bracket algebra (for internal use)
  * `point_ordering::Vector{Int}`: ordering of the `n` point indices, that induces the tableaux order. `point_ordering[1] < point_ordering[2] < ... < point_ordering[n]`.
  * `variables::Bijection{Vector{Int},<:MPolyRingElem{T}}`: bijection from brackets to the corresponding monomials in the polynomial ring `R`
  * `point_labels::Vector`: point labels for each point
