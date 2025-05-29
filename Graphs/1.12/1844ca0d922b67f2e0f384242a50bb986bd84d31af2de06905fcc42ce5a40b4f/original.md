```
self_avoiding_walk(g, s, niter; rng=nothing, seed=nothing)
```

Perform a [self-avoiding walk](https://en.wikipedia.org/wiki/Self-avoiding_walk) on graph `g` starting at vertex `s` and continuing for a maximum of `niter` steps. Return a vector of vertices visited in order.
