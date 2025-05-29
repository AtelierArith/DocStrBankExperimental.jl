```
weyldot(f::Polynomial, g::Polynomial)
```

Compute the [Bombieri-Weyl dot product](https://en.wikipedia.org/wiki/Bombieri_norm). Note that this is only properly defined if `f` and `g` are homogenous.

```
weyldot(f::Vector{Polynomial}, g::Vector{Polynomial})
```

Compute the dot product for vectors of polynomials.
