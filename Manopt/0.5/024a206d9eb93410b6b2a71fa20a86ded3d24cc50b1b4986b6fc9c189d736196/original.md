```
get_cost(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p, i)
```

Evaluate the `i`th summand of the cost.

If you use a single function for the stochastic cost, then only the index `ì=1`` is available to evaluate the whole cost.
