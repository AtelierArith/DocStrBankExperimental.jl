```
pseudoabsencemask( ::Type{DistanceToEvent}, presences::SDMLayer{Bool}; f = minimum, )
```

Generates a mask for pseudo-absences using the distance to event method. Candidate cells are weighted according to their distance to a known observation, with far away places being more likely. Depending on the distribution of distances, it may be a very good idea to flatten this layer using `log` or an exponent. The `f` function is used to determine which distance is reported (`minimum` by default, but can be any other relevant function).
