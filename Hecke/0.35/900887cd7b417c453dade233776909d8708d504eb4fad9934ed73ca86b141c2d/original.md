```
brown_invariant(self::TorQuadModule) -> Nemo.zzModRingElem
```

Return the Brown invariant of this torsion quadratic form.

Let `(D,q)` be a torsion quadratic module with values in `Q / 2Z`. The Brown invariant `Br(D,q) in Z/8Z` is defined by the equation

$$
\exp \left( \frac{2 \pi i }{8} Br(q)\right) =
  \frac{1}{\sqrt{D}} \sum_{x \in D} \exp(i \pi q(x)).
$$

The Brown invariant is additive with respect to direct sums of torsion quadratic modules.

# Examples

```jldoctest
julia> L = integer_lattice(gram=matrix(ZZ, [[2,-1,0,0],[-1,2,-1,-1],[0,-1,2,0],[0,-1,0,2]]));

julia> T = Hecke.discriminant_group(L);

julia> brown_invariant(T)
4
```
