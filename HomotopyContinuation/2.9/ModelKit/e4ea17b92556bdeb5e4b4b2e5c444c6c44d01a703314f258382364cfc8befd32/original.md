```
TaylorVector{N,T}
```

A data structure representing a vector of Taylor series with `N` terms. Each element is an `NTuple{N,T}`.

```
TaylorVector(T, N::Integer, n::Integer)
```

Create a vector of `n` `NTuple{N,T}`s.
