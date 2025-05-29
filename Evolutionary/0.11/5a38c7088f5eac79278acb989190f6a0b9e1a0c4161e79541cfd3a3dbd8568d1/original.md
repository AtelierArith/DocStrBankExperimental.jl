```
roulette(fitness)
```

Roulette wheel (fitness proportionate, FPS) selection from `fitness` collection.

In roulette selection, the fitness level is used to associate a probability of selection with each individual. If $f_i$ is the fitness of individual $i$ in the population, its probability of being selected is $p_i = \frac{f_i}{\Sigma_{j=1}^{M} f_j}$, where $M$ is the number of individuals in the population.

*Note:* Best used in maximization context.
