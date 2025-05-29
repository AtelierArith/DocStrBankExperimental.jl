```
abstract type AbstractSD
```

AbstractSD represents an abstract bath spectral density.

Any subtype of `AbstractSD` must at least define either `sd` or `sdoverω` for the new type.
