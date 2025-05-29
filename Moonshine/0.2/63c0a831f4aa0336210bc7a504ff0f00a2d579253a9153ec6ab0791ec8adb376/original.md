```
CoalMutDensity
```

Density of a genealogy with mutations according to the coalescent. Mutations are assumed to be selection neutral i.e. independent of the coalescent process.

See also [`CoalDensity`](@ref).

# Fields

  * `fC::CoalDensity`: density of the genealogy (excluding mutations)
  * `Ne::BigFloat`: effective population size
  * `μ_loc::BigFloat`: per locus mutation rate
  * `seq_length`: length of the sequences
