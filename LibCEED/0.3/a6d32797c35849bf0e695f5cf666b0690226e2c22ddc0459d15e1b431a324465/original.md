```
getgrad(b::Basis)
```

Get the gradient matrix of the given [`Basis`](@ref). Returns a tensor of size `(getdimension(b), getnumqpts(b), getnumnodes(b))`.
