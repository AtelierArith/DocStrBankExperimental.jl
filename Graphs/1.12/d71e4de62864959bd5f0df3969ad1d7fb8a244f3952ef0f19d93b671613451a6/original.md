```
diffusion(g, p, n)
```

Run diffusion simulation on `g` for `n` steps with spread probabilities based on `p`. Return a vector with the set of new vertices reached at each step of the simulation.

### Optional Arguments

  * `initial_infections=sample(vertices(g), 1)`: A list of vertices that

are infected at the start of the simulation.

  * `watch=Vector()`: While simulation is always run on the full graph,

specifying `watch` limits reporting to a specific set of vertices reached during the simulation. If left empty, all vertices will be watched.

  * `normalize=false`: if `false`, set the probability of spread from a vertex $i$ to

each of the outneighbors of $i$ to $p$. If `true`, set the probability of spread from a vertex $i$ to each of the `outneighbors` of $i$ to $\frac{p}{outdegreee(g, i)}$.

  * `rng=nothing`: A random generator to sample from.
