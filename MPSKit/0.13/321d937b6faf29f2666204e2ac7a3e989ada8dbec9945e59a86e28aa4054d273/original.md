```
entropy(state, [site::Int])
```

Calculate the Von Neumann entanglement entropy of a given MPS. If an integer `site` is given, the entropy is across the entanglement cut to the right of site `site`. Otherwise, a vector of entropies is returned, one for each site.
