```
map_coefficients(f, p::SeriesElem{<: RingElement}; cached::Bool=true, parent::PolyRing)
```

Transform the series `p` by applying `f` on each non-zero coefficient.

If the optional `parent` keyword is provided, the polynomial will be an element of `parent`. The caching of the parent object can be controlled via the `cached` keyword argument.
