```
Polytope{N}(p::Polytope,faceid::Integer) where N
```

Returns a `Polytope{N}` object representing the "reference" polytope of the `N`-face with id `faceid`. The value `faceid` refers to the numeration restricted to the dimension `N` (it starts with 1 for the first `N`-face).
