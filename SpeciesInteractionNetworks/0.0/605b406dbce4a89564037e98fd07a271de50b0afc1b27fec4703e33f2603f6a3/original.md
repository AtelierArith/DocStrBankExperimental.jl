```
nullmodel(::Type{Degree}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

Returns a probabilistic network under the null model that all interactions occurr with a probability equal to the average of their generality and vulnerability, *i.e.* proportionally to how many links the species involved are establishing:

$P(i \rightarrow j) = \frac{1}{2}\left(\frac{\sum A_{i \rightarrow \cdot}}{|B|} + \frac{\sum A_{\cdot \rightarrow j}}{|T|} \right)$

###### References

[Bascompte2003nested](@citet*)
