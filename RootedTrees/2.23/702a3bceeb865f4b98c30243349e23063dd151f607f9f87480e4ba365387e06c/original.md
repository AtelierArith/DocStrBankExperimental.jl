```
ColoredRootedTree(level_sequence, color_sequence, is_canonical::Bool=false)
```

Represents a colored rooted tree using its level sequence. The single-colored version is [`RootedTree`](@ref).

See also [`BicoloredRootedTree`](@ref), [`rootedtree`](@ref).

!!! warning
    This is a low-overhead and unsafe constructor. Please consider calling [`rootedtree`](@ref) instead.


# References

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
  * A. L. Araujo, A. Murua, and J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926–1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)
