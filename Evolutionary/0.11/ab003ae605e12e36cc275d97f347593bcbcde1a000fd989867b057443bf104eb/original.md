```
ranklinear(sp::Real)
```

Returns a rank-based fitness selection function, see [Selection Interface](@ref), with the selective pressure value `sp`.

In rank-based fitness selection, the population is sorted according to the objective values. The fitness assigned to each individual depends only on its position in the individuals rank and not on the actual objective value [^1].

Consider $M$ the number of individuals in the population, $P$ the position of an individual in this population (least fit individual has $P = 1$, the fittest individual $P = M$) and $SP$ the selective pressure. The fitness value for an individual is calculated as:

$Fitness(P) = 2 - SP + \frac{2(SP - 1)(P - 1)}{(M - 1)}$

Linear ranking allows values of selective pressure in [1.0, 2.0].
