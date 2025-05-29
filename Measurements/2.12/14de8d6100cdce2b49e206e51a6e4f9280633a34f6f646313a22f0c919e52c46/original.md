```
measurement(val::Real, [err::Real]) -> Measurement
measurement(::Missing, [err::Union{Real,Missing}]) -> Missing
val ± err -> Measurement
```

Return a `Measurement` object with `val` as nominal value and `err` as uncertainty.  `err` defaults to 0 if omitted.

The binary operator `±` is equivalent to `measurement`, so you can construct a `Measurement` object by explicitly writing `123 ± 4`.

If `val` is `missing`, `missing` is returned.
