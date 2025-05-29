```
specificity(N::SpeciesInteractionNetwork{<:Partiteness, <:Union{Binary,Quantitative}})
```

For a deterministic network, this function will return a dictionary mapping each top-level species to its specificity. The same index (Paired Differences Index) is used for binary and quantitative networks. A value of one corresponds to maximum specialism, and a value of zero to maximum generalism. The index is symmetrical, so that a species with a value of one half is neither specialist nor generalist.

###### References

[Poisot2012comparative](@citet*)
