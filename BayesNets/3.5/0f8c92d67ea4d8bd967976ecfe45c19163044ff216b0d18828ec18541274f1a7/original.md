```
bayesian_score(G::DAG, names::Vector{Symbol}, data::DataFrame[, ncategories::Vector{Int}[, prior::DirichletPrior]])
```

Compute the bayesian score for graph structure `g`, with the data in `data`. `names` containes a symbol corresponding to each vertex in `g` that is the name of a column in `data`. `ncategories` is a vector of the number of values that each variable in the Bayesian network can take.

Note that every entry in data must be an integer greater than 0
