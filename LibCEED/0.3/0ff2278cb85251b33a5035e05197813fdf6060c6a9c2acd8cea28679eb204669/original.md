```
getinterp1d(b::Basis)
```

Get the 1D interpolation matrix of the given [`Basis`](@ref). `b` must be a tensor-product basis, otherwise this function will fail. Returns a matrix of size `(getnumqpts1d(b), getnumnodes1d(b))`.
