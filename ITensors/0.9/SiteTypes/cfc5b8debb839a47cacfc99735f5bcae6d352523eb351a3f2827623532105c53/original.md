```
siteinds(f::Function, N::Integer; kwargs...)
```

Create an array of `N` physical site indices where the site type at site `n` is given by `f(n)` (`f` should return a string).
