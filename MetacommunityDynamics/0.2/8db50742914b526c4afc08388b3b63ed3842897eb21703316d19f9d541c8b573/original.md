```
BevertonHolt{S} <: Model{Population,Biomass,S,Discrete}
```

The [Beverton-Holt model](https://en.wikipedia.org/wiki/Beverton%E2%80%93Holt_model) is a discrete-time, deterministic model of population dynamics. It is commonly interpreted as a discrete-time version of the logistic model.

It is described by 

$N_{t+1} =\frac{R_0 M}{N_t + M}N_t$

where $K = (R\_0 - 1)M$ is the carrying capacity.
