```
RootedTree(level_sequence, is_canonical::Bool=false)
```

Represents a rooted tree using its level sequence.

!!! warning
    This is a low-overhead and unsafe constructor. Please consider calling [`rootedtree`](@ref) instead.


# References

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
