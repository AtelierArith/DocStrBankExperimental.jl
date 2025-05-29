```
module DifferentiableMetabolism
```

Differentiate parameterized genome-scale metabolic models. Currently, `FastDifferentiation` parameters are used in conjunction with `COBREXA` models. To ensure your derivatives are well defined, you must ensure that the models are *pruned*, i.e. all active reactions, genes, etc. have nonzero values at the optimum. See the documentation for model details and examples.
