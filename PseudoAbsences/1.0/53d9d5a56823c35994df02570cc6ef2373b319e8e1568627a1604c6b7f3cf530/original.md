```
pseudoabsencemask(::Type{RandomSelection}, presences::SDMLayer{Bool})
```

Generates a mask for pseudo-absences using the random selection method. Candidate cells for the pseudo-absence mask are (i) within the bounding box of the *layer* (use `SurfaceRangeEnvelope` to use the presences bounding box), and (ii) valued in the layer.
