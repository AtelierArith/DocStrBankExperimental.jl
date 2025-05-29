```
nodf(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork,BipartiteQuantitativeNetwork}}
```

Returns `nodf` for a margin of the network. The `i` argument can be 1 for top-level, 2 for bottom level, and the function will throw an `ArgumentError` if an invalid value is used. For quantitative networks, *WNODF* is used.

#### References

Almeida-Neto, M., Guimarães, P.R., Loyola, R.D., Ulrich, W., 2008. A consistent metric for nestedness analysis in ecological systems: reconciling concept and measurement. Oikos 117, 1227–1239. https://doi.org/10.1111/j.0030-1299.2008.16644.x

Almeida-Neto, M., Ulrich, W., 2011. A straightforward computational approach for measuring nestedness using quantitative matrices. Environmental Modelling & Software 26, 173–178. https://doi.org/10.1016/j.envsoft.2010.08.003
