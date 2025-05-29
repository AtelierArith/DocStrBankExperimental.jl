```julia
shrinkFactorGraph(fg; upto)

```

Prunes factor graph to keep up to `upto` number of variables.

Warning: uses functions that are outside of IncrementalInference (e.g., `isSolvable()`), so will probably need to place this elsewhere.
