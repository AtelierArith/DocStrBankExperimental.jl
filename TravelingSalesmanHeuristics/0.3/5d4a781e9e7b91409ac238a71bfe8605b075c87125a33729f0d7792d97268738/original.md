```
lowerbound(distmat)
```

Lower bound the cost of the optimal TSP tour. At present, the bounds considered are a simple bound based on the minimum cost of entering and exiting each city and a slightly better bound inspired by the Held-Karp bounds; note that the implementation here is simpler and less tight than proper HK bounds.

The Held-Karp-inspired bound requires computing many spanning trees. For a faster but typically looser bound, use `TravelingSalesmanHeuristics.vertwise_bound(distmat)`.

!!! note
    The spanning tree bounds are only correct on symmetric problem instances and will not be used if the passed `distmat` is not symmetric. If you wish to use these bounds anyway, (e.g. for near-symmetric instances), use `TravelingSalesmanHeuristics.hkinspired_bound`.

