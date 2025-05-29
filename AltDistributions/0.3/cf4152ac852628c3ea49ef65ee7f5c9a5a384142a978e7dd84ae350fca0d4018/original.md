```
Fixed(value)
```

Wrapper type to signal that `value` is "fixed" for the purposes of a log density calculation. Formally,

```julia
logpdf(d, Fixed(v)) == logpdf(d, v) + C
```

where `C` is a constant term that only depends on `v`. In other words,

```julia
logpdf(distribution(θ), Fixed(v)) - logpdf(distribution(θ′), Fixed(v))
```

should always be correctly calculated. Use `get(Fixed(value)` to access the value.
