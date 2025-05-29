```
genpars(D)
```

Returns the genetical parameters associated with a density in the form of a named tuple.

# Names

Names of the parameters are standardized as follow:

  * `seq_length`: length of the haplotypes
  * `Ne`: effective population size
  * `μloc`: per locus mutation rate
  * `ρloc`: per locus recombination rate
  * `positions`: positions of the markers normalized in [0, 1]
