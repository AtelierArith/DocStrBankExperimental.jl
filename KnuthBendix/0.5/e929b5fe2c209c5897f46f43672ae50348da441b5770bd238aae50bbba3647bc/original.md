```
WreathOrder{T,S} <: RewritingOrdering
WreathOrder(A::Alphabet; levels[, order=collect(A)])
```

Compare words first by their levels, then break ties by recursion on prefixes.

The `levels` vector assigns levels to each letter **as they appear in the alphabet** and the `level` of a word is the maximum of levels of all its letters.

The order compare words first by their levels, then break ties by `LenLex` order of pure max-level words. Further ties are resolved by recursing on lower level prefixes.

# Definition

Let `U = U₀·a₁·U₁·…·aᵣ·Uᵣ` be a decomposition of `U` such that

  * all `aᵢ`s are at the same (maximal) level and
  * each `Uᵢ` is at level strictly smaller.

Let `V = V₀·b₁·V₁·…·bₛ·Vₛ` be a similar decomposition. Then `U <≀ V` if either

  * `a₁·…·aᵣ < b₁·…·bₛ` according to `LenLex` order, or
  * `a₁·…·aᵣ = b₁·…·bₛ` and `U₀ <≀ V₀`, or `Uᵢ = Vᵢ` for `0≤i<k` but `Uₖ <≀ Vₖ`.

For more references see

> 1. C. Sims *Computation with finitely presented groups*, p. 46-47
> 2. D. Holt, B. Eick and E. O’Brien *Handbook of Computational Group Theory*, Section 12.4 Rewriting systems for polycyclic groups, p. 426-427
> 3. S. Rees *Automatic groups associated with word orders other than shortlex* Section 5.3 Wreath product orders.


# Example

```jldoctest
julia> X = Alphabet([:a, :b]);

julia> a, b = Word([1]), Word([2]);

julia> wro = WreathOrder(X, levels = [1, 2])
WreathOrder: a(1) < b(2)

julia> lt(wro, a^100, a * b * a^2) # by level only
true

julia> lt(wro, b^2*a, a^2 * b * a) # by max-level word
false

julia> lt(wro, a * b * a^2, a^2 * b * a) # by the lower level prefix
true
```
