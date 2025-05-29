```
primes(G::ZZGenus) -> Vector{ZZRingElem}
```

Return the list of primes of the local symbols of `G`.

Note that 2 is always in the output since the 2-adic symbol of a `ZZGenus` is, by convention, always defined.
