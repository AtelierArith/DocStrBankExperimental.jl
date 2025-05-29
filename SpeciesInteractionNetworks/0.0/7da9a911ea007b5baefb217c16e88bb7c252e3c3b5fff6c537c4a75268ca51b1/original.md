```
nullmodel(::Type{Generality}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

Returns a probabilistic network under the null model that interactions happen proportionally to the vulnerability of the species, *i.e.* their expected number of incomin links:

$P(i \rightarrow j) = \frac{\sum A_{\cdot \rightarrow j}}{|T|}$

###### References

[Poisot2013Facultative](@citet*)

[Weitz2013Phagebacteria](@citet*)
