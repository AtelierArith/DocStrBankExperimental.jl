```
permutationtest(perm::MixedModelPermutation, model, type=:greater)
```

Perform a permutation using the already computed permutation and given the observed values.

The `type` parameter specifies use of a two-sided test (`:twosided`) or the directionality of a one-sided test (either `:lesser` or `:greater`, depending on the hypothesized difference to the null hypothesis).

See also [`permutation`](@ref).

To account for finite permutations, we implemented the conservative method from Phipson & Smyth 2010:  Permutation P-values Should Never Be Zero:Calculating Exact P-values When Permutations Are Randomly Drawn  http://www.statsci.org/webguide/smyth/pubs/permp.pdf 
