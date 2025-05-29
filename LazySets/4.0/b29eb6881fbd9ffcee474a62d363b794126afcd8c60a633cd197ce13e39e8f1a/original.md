```
remove_redundant_generators(Z::AbstractZonotope)
```

Remove all redundant (pairwise linearly dependent) generators of a zonotopic set.

### Input

  * `Z` – zonotopic set

### Output

A new zonotope with fewer generators, or the same zonotopic set if no generator could be removed.

### Algorithm

By default this implementation returns the input zonotopic set. Subtypes of `AbstractZonotope` whose generators can be removed have to define a new method.
