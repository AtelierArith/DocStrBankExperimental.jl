```
CoupledVariable(element::Asap.FDMelement, ref::QVariable, factor::Float64 = 1.0)
```

Make an `Qvariable` for `element` that is coupled to `factor * ref.value`

`factor` must be > 0.
