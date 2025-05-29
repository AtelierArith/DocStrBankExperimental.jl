```
getinterp(b::Basis)
```

Get the interpolation matrix of the given [`Basis`](@ref). Returns a matrix of size `(getnumqpts(b), getnumnodes(b))` for a given $H^1$ basis or `(getdimension(b), getnumqpts(b), getnumnodes(b))` for a given vector $H(div)$ or $H(curl)$ basis.
