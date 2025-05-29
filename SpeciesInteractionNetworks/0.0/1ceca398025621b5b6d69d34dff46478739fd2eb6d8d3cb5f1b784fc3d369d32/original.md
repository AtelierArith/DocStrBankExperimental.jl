```
nullmodel(::Type{Generality}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

Returns a probabilistic network under the null model that interactions happen proportionally to the generality of the species, *i.e.* their expected number of outgoing links:

$P(i \rightarrow j) = \frac{\sum A_{i \rightarrow \cdot}}{|B|}$

###### References

[Poisot2013Facultative](@citet*)

[Weitz2013Phagebacteria](@citet*)
