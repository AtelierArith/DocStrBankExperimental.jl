```
static_fitness_model(m, fitness, G=Graph; seed=-1)
static_fitness_model(m, fitness_out, fitness_in, G=DiGraph; seed=-1)
```

Generates a random graph with `length(fitness)` nodes and `m` edges, in which the probability of the existence of edge `(i, j)` is proportional to `fitness[i]*fitness[j]`. Time complexity is O(|V| + |E| log |E|).

In and out fitness have to be supplied for generating directed graphs.

Reference:

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution

in scale-free networks. Phys Rev Lett 87(27):278701, 2001.
