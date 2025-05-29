```
siteinds(M::MPS)
siteinds(::typeof(first), M::MPS)
```

Get a vector of the first site Index found on each tensor of the MPS.

```
siteinds(::typeof(only), M::MPS)
```

Get a vector of the only site Index found on each tensor of the MPS. Errors if more than one is found.

```
siteinds(::typeof(all), M::MPS)
```

Get a vector of the all site Indices found on each tensor of the MPS. Returns a Vector of IndexSets.
