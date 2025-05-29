```
pseudoabsencemask(::Type{SurfaceRangeEnvelope}, presences::SDMLayer{Bool})
```

Generates a mask from which pseudo-absences can be drawn, by picking cells that are (i) within the bounding box of occurrences, (ii) valued in the layer, and (iii) not already occupied by an occurrence
