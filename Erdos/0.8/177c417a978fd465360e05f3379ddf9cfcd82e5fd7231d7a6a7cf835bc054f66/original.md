```
static_scale_free(n, m, α, G=Graph;
                seed=-1, finite_size_correction=true)
```

Generates a random graph with `n` vertices, `m` edges and expected power-law degree distribution with exponent `α`. `finite_size_correction` determines whether to use the finite size correction proposed by Cho et al. This generator calls internally the `static_fitness_model function`. Time complexity is O(|V| + |E| log |E|).

```
static_scale_free(n, m, α_out, α_in, G=DiGraph;
                seed=-1, finite_size_correction=true)
```

Generates a random digraph.

References:

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution in scale-free networks. Phys Rev Lett 87(27):278701, 2001.
  * Chung F and Lu L: Connected components in a random graph with given degree sequences. Annals of Combinatorics 6, 125-145, 2002.
  * Cho YS, Kim JS, Park J, Kahng B, Kim D: Percolation transitions in scale-free networks under the Achlioptas process. Phys Rev Lett 103:135702, 2009.
