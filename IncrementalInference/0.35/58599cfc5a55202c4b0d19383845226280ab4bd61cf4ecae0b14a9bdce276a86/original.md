```julia
mutable struct MetaBayesTree <: IncrementalInference.AbstractBayesTree
```

Data structure for the Bayes (Junction) tree, which is used for inference and constructed from a given `::AbstractDFG`.
