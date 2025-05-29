```
CoupledVariable(element::Asap.AbstractElement, ref::AreaVariable, factor::Float64 = 1.0)
```

Make an `AreaVariable` for `element` that is coupled to `factor * ref.value`

`factor` must be > 0.
