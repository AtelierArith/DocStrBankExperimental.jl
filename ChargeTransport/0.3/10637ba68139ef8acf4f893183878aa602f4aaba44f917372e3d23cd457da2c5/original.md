```julia
flux!(f, u, edge, data) -> Any

```

Master flux functions which enters VoronoiFVM. Flux discretization scheme is chosen in two steps. First, we need to see, if we are in or out of equilibrium. If, InEquilibrium, then no flux is passed. If outOfEquilibrium, we choose the flux approximation which the user chose for each charge carrier. For the displacement flux we use a finite difference approach.
