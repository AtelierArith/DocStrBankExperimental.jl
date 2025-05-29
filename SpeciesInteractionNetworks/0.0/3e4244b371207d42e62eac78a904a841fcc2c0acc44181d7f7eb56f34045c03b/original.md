```
spectralradius(N::SpeciesInteractionNetwork{<:Unipartite, <:Binary}; correction=:links)
```

The spectral radius of a unipartite is a conceptual equivalent to nestedness [Staniczenko2013ghost](@cite). It is defined as the absolute value of the largest real part of the eigenvalues of the *undirected* adjacency matrix.

There are a number of corrections available through the `correction` keyword.

The default correction is `:links` as in [Staniczenko2013ghost](@citet), where the values are divided by the square root of the number of links, *excluding the self-interactions*.

Using the `:connectance` correction follows the version of [Phillips2011structure](@citet), where the values are divided by the square root of $(L\times(S-1))S^{-1}$ (this is not *quite* connectance, but the point is that this version is corrected for network size and order).

Using `:none` returns the raw values, and for the sake of comparisons across networks, it is advised not to use it. It is included for cases where the networks to compare have the same number of species and interactions, as in this case it is appropriate and slightly faster than other corrections.

###### References

[Phillips2011structure](@citet*)

[Staniczenko2013ghost](@citet*)
