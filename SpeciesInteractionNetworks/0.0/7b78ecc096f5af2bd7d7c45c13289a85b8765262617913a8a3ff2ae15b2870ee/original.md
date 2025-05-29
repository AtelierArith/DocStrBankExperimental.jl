```
rdpg(N::SpeciesInteractionNetwork, r::Integer)
```

Returns a quantitative network predicted using a random dot-product graph on the [`tsvd`](@ref) of the network at rank `r`.

RDPG has been shown to be predictive of food web structure even in the context of transfer learning [Strydom2022Food](@cite).

###### References

[DallaRiva2016Exploring](@citet*)

[Strydom2022Food](@citet*)
