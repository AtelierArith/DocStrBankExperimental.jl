```
change_coefficient_ring(R::Ring, p::PolyRingElem{<: RingElement}; parent::PolyRing)
```

Return the polynomial obtained by coercing the non-zero coefficients of `p` into `R`.

If the optional `parent` keyword is provided, the polynomial will be an element of `parent`. The caching of the parent object can be controlled via the `cached` keyword argument.
