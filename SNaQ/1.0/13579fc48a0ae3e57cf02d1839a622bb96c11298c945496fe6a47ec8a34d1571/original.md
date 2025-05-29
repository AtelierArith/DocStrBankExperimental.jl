```
Quartet
```

type that saves the information on a given 4-taxon subset. It contains the following attributes:

  * `number`: integer
  * `taxon`: vector of taxon names, like t1 t2 t3 t4
  * `obsCF`: vector of observed CF, in order 12|34, 13|24, 14|23
  * `logPseudoLik`
  * `ngenes`: number of gene trees used to compute the observed CF; -1.0 if unknown
  * `qnet`: [`QuartetNetwork`](@ref), which saves the expCF after snaq estimation to emphasize that the expCF depend on a specific network, not the data

see also: [`PhyloNetworks.QuartetT`](@extref) for quartet with data of user-defined type `T`, using a mapping between quartet indices and quartet taxa.
