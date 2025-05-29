```
transform(op::SymOperation, P::AbstractMatrix{<:Real}, 
          p::Union{AbstractVector{<:Real}, Nothing}=nothing,
          modw::Bool=true)                           --> SymOperation
```

Transforms a `op` $= \{\mathbf{W}|\mathbf{w}\}$ by a rotation matrix `P` and a translation vector `p` (can be `nothing` for zero-translations), producing a new symmetry operation  `op′` $= \{\mathbf{W}'|\mathbf{w}'\}$ (cf. Section 1.5.2.3 of [^ITA6])

$$
\{\mathbf{W}'|\mathbf{w}'\} = \{\mathbf{P}|\mathbf{p}\}^{-1}\{\mathbf{W}|\mathbf{w}\}
\{\mathbf{P}|\mathbf{p}\}
$$

with

$$
\mathbf{W}' = \mathbf{P}^{-1}\mathbf{W}\mathbf{P}
\text{ and }
\mathbf{w}' = \mathbf{P}^{-1}(\mathbf{w}+\mathbf{W}\mathbf{p}-\mathbf{p})
$$

By default, the translation part of `op′`, i.e. $\mathbf{w}'$, is reduced to the range $[0,1)$, i.e. computed modulo 1. This can be disabled by setting `modw = false` (default, `modw = true`).

See also [`Bravais.primitivize(::SymOperation, ::Char, ::Bool)`](@ref) and [`Bravais.conventionalize(::SymOperation, ::Char, ::Bool)`](@ref).

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016).
