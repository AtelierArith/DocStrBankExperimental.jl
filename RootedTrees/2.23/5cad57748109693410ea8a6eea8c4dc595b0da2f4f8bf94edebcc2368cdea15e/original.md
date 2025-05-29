```
rootedtree!(level_sequence)
```

Construct a canonical [`RootedTree`](@ref) object from a `level_sequence` which may be modified in this process. See also [`rootedtree`](@ref).

!!! warning
    This may modify the `level_sequence` and further modifications of the `level_sequence` may invalidate the rooted tree returned by this function. Please consider calling [`rootedtree`](@ref) instead.


# References

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
