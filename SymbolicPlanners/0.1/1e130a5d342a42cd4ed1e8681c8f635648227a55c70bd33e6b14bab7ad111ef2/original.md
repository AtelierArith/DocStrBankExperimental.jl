```
memoized(h::Heuristic)
```

Constructs a memoized version of `h` which caches outputs in a hash table after each evaluation of the heuristic on a new domain, state, or specification.
