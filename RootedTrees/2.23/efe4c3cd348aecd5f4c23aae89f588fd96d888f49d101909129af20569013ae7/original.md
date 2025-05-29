```
rootedtree(level_sequence, color_sequence)
```

Construct a canonical [`ColoredRootedTree`](@ref) object from a `level_sequence` and a `color_sequence`, i.e., a vector of integers representing the levels of each node of the tree and a vector of associated colors (e.g., `Bool`s or `Integers`).

# References

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
