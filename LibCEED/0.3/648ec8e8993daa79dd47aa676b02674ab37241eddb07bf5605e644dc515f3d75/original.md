```
getgrad1d(b::Basis)
```

Get the 1D derivative matrix of the given [`Basis`](@ref). Returns a matrix of size `(getnumqpts(b), getnumnodes(b))`.
