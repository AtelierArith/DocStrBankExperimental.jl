```
canonicaldomain([ctype::CanonicalType, ]d)
```

Return an associated canonical domain, if any, of the given domain.

For example, the canonical domain of an Interval `[a,b]` is the interval `[-1,1]`.

Optionally, a canonical type argument may specify an alternative canonical domain. Canonical domains help with establishing equality between domains, with finding maps between domains and with finding parameterizations.

If a domain implements a canonical domain, it should also implement `mapfrom_canonical` and `mapto_canonical`.

See also: [`mapfrom_canonical`](@ref), [`mapto_canonical`](@ref).
