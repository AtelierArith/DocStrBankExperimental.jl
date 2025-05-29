```
BravaisTranslation([site_indices, ]translate_uc)
BravaisTranslation(site_indices)
BravaisTranslation([site_indices; ]axis[, dist=1])
```

A convenient constructor for a `BravaisTranslation` object.

## Arguments

  * `site_indices`: a `::Int => ::Int` pair with indices of sites connected by the bond;

if omitted, the bond connects sites with the same sublattice index.

  * `translate_uc`: The unit cell offset.

## Keyword arguments

  * `axis`: The hopping direction axis in terms of unit cell vectors.
  * `dist`: The hopping distance in terms of unit cell vectors.

If `site_indices` are equal or undefined and `translate_uc` is zero, the translation is considered to be a translation of all sites to themselves. An error will be thrown in this case.
