```
merge_cliques!(cg::CliqueGraph; verbose=false)
```

Merges cliques in `cg` in a greedy fashion starting with the pair with the largest `weight_function`. Stops when all pairs of cliques have a non-positive weight.

# Reference

  * [A clique graph based merging strategy for decomposable SDPs](https://arxiv.org/pdf/1911.05615) by Michael Garstka, Mark Cannon, Paul Goulart
