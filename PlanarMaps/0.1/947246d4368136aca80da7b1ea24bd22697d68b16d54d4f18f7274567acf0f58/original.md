```
allwoods(P::PlanarMap,C::Channel)
```

Send a sequence of all `WoodedTriangulation`s on `P` to the channel `C`

# Examples:

```julia
# Count the number of Schnyder woods on a
# a randomly sampled wooded triangulation of size 10
sum(1 for W in Channel(C->allwoods(PlanarMap(UWT(10)),C)))
```
