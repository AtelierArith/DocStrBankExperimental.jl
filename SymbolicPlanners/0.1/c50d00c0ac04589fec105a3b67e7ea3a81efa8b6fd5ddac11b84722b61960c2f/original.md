```
precomputed(h::Heuristic, domain::Domain, args...)
```

Precomputes a heuristic in advance, returning a [`PrecomputedHeuristic`](@ref) that prevents repeated pre-computation later.
