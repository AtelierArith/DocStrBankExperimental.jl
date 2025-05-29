```
change_base_ring(R::Ring, p::SeriesElem{<: RingElement}; parent::PolyRing)
```

Return the series obtained by coercing the non-zero coefficients of `p` into `R`.

If the optional `parent` keyword is provided, the series will be an element of `parent`. The caching of the parent object can be controlled via the `cached` keyword argument.
