```
static_scale_free(n, m, α)
```

Generate a random graph with `n` vertices, `m` edges and expected power-law degree distribution with exponent `α`.

### Optional Arguments

  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.
  * `finite_size_correction=true`: determines whether to use the finite size correction

proposed by Cho et al.

### Performance

Time complexity is $\mathcal{O}(|V| + |E| log |E|)$.

### References

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution in scale-free networks. Phys Rev Lett 87(27):278701, 2001.
  * Chung F and Lu L: Connected components in a random graph with given degree sequences. Annals of Combinatorics 6, 125-145, 2002.
  * Cho YS, Kim JS, Park J, Kahng B, Kim D: Percolation transitions in scale-free networks under the Achlioptas process. Phys Rev Lett 103:135702, 2009.
