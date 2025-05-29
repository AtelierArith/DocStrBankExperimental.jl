```
struct SignSymmetry <: Sparsity.Pattern end
```

Sign symmetry as developed in [Section III.C, L09]. Let `n` be the number of variables. A *sign-symmetry* is a binary vector `r` of `{0, 1}^n` such that `dot(r, e)` is even for all exponent `e`.

Let `o(e)` be the binary vector of `{0, 1}^n` for which the `i`th bit is `i` iff the `i`th entry of `e` is odd. Let `O` be the set of `o(e)` for exponents of `e`. A binary vector `r` is a sign-symmetry if an only if it is orthogonal to all the elements of `O`.

Since we are only interested in the orthogonal subspace, say `R`, of `O`, even if `O` is not a linear subspace (i.e., it is not invariant under `xor`), we compute its span. We start by creating row echelon form of the span of `O` using [`XORSpace`](@ref). We then compute a basis for `R`. The set `R` of sign symmetries will be the span of this basis.

Let `a`, `b` be exponents of monomials of the gram basis. For any `r in R`,

```
⟨r, o(a + b)⟩ = ⟨r, xor(o(a), o(b)⟩ = xor(⟨r, o(a)⟩, ⟨r, o(b)⟩)
```

For `o(a, b)` to be sign symmetric, this scalar product should be zero for all sign symmetry `r`. This is equivalent to saying that `⟨r, o(a)⟩` and `⟨r, o(b)⟩` are equal for all `r in R`. In other words, the projection of `o(a)` and `o(b)` to `R` have the same coordinates in the basis. If we order the monomials by grouping them by equal coordinates of projection, we see that the product that are sign symmetric form a block diagonal structure. This means that we can group the monomials by these coordinates.

[L09] Löfberg, Johan. *Pre-and post-processing sum-of-squares programs in practice*. IEEE transactions on automatic control 54, no. 5 (2009): 1007-1011.
