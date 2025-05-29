**Univariate**

```
computeSP(a::AbstractVector{<:Integer},α::AbstractVector{<:Real},β::AbstractVector{<:Real},nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real};issymmetric::Bool=false)
computeSP(a::AbstractVector{<:Integer},op::AbstractOrthoPoly;issymmetric=issymmetric(op))
```

**Multivariate**

```
computeSP( a::AbstractVector{<:Integer},
           α::AbstractVector{<:AbstractVector{<:Real}},β::AbstractVector{<:AbstractVector{<:Real}},
           nodes::AbstractVector{<:AbstractVector{<:Real}},weights::AbstractVector{<:AbstractVector{<:Real}},
           ind::AbstractMatrix{<:Integer};
           issymmetric::BitArray=falses(length(α)))
computeSP(a::AbstractVector{<:Integer},op::AbstractVector,ind::AbstractMatrix{<:Integer})
computeSP(a::AbstractVector{<:Integer},mOP::MultiOrthoPoly)
```

Computes the scalar product

$$
\langle \phi_{a_1},\phi_{a_2},\cdots,\phi_{a_n} \rangle,
$$

where `n = length(a)`. This requires to provide the recurrence coefficients `(α,β)` and the quadrature rule `(nodes,weights)`, as well as the multi-index `ind`. If provided via the keyword `issymmetric`, symmetry of the weight function is exploited. All computations of the multivariate scalar products resort back to efficient computations of the univariate scalar products. Mathematically, this follows from Fubini's theorem.

The function is dispatched to facilitate its use with `AbstractOrthoPoly` and its quadrature rule `Quad`.

!!! note
      * Zero entries of $a$ are removed automatically to simplify computations, which follows from

    $$
    \langle \phi_i, \phi_j, \phi_0,\cdots,\phi_0 \rangle = \langle \phi_i, \phi_j \rangle,
    $$

    because `\phi_0 = 1`.

      * It is checked whether enough quadrature points are supplied to solve the integral exactly.

