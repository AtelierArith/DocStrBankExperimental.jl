```
η(N::T, dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork, BipartiteProbaNetwork}}
```

Returns the nestedness of a margin of the network, using η. The second argument can be `1` (for nestedness of rows/top level) or `2` (for nestedness of columns/bottom level). Leaving it at `nothing` will measure the nestedness of the entire network.

#### References

  * Bastolla, U., Fortuna, M.A., Pascual-García, A., Ferrera, A., Luque, B., Bascompte, J., 2009. The architecture of mutualistic networks minimizes competition and increases biodiversity. Nature 458, 1018–1020. https://doi.org/10.1038/nature07950
  * Poisot, T., Cirtwill, A.R., Cazelles, K., Gravel, D., Fortin, M.-J., Stouffer, D.B., 2016. The structure of probabilistic networks. Methods in Ecology and Evolution 7, 303–312. https://doi.org/10.1111/2041-210X.12468
