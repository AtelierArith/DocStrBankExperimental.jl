```
bat_integrated_autocorr_len(
    v::_ACLenTarget,
    algorithm::AutocorLenAlgorithm = GeyerAutocorLen(),
    [context::BATContext]
)
```

*Experimental feature, not yet part of stable public API.*

Estimate the integrated autocorrelation length of variate series `v`, separately for each degree of freedom.

Returns a NamedTuple of the shape

```julia
(result = integrated_autocorr_len, ...)
```

Result properties not listed here are algorithm-specific and are not part of the stable public API.

!!! note
    Do not add add methods to `bat_integrated_autocorr_len`, add methods to `bat_integrated_autocorr_len_impl` instead.

