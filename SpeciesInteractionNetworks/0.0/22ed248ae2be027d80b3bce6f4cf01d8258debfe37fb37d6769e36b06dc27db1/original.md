```
labelpropagation(N::SpeciesInteractionNetwork)
```

Uses label propagation to generate a first approximation of the modular structure of a network. This is usually followed by the BRIM (`brim`) method. This method supposedly performs better for large graphs, but we rarely observed any differences between it and variations of BRIM alone on smaller graphs.

###### References

[Liu2010Community](@citet*)
