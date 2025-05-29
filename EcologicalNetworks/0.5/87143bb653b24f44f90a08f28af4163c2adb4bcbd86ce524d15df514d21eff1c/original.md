```
distance_to_producer(N::UnipartiteNetwork; f=maximum)
```

Returns the distance from a primary producert of every species in the food web. Primary producers have a trophic level of 1, after that, it's complicated (see *e.g.* Williams & Martinez 2004, Thompson et al. 2007).

Post (2002) notes that the trophic level can be obtained from the maximum, mean, or minimum distance to a producer. Given that consumers may be connected to more than one producer, one might argue that the *mode* of this distribution is also relevant.

In favor of the minimum, one can argue that most energy transfer should happen along short chains; but imagining a consumer atop a chain of length 5, also connected directly to a producer, the minimum would give it a trophic level of 2, hiding its position at the top of the food web.

In favor of the maximum, one can argue that the higher chains give a better idea of how far energy coming from the bottom of the food web can go. This is a strong indication of how *vertically* diverse it is.

In this package, the keyword `f` defaults to `maximum`. Using any other function, as long as it accepts an array (of chain distances) and return a scalar, will work; `minimum` and `Statistics.mean` are natural alternatives, as is `StatsBase.mode` or `Statistics.median`.

The chain length from any species to any producer is taken as the shortest possible path between these two species, as identified by the Dijkstra algorithm.
