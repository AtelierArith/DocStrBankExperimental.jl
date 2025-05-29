```
transformed(d::Distribution)
transformed(d::Distribution, b::Bijector)
```

Couples distribution `d` with the bijector `b` by returning a `TransformedDistribution`.

If no bijector is provided, i.e. `transformed(d)` is called, then  `transformed(d, bijector(d))` is returned.
