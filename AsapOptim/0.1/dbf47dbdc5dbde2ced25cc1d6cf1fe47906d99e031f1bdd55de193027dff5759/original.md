```
CoupledVariable(element::Asap.Element, ref::T, factor::Float64 = 1.0) where {T<:SectionVariable}
```

Make an `SectionVariable` for `element` that is coupled to `factor * ref.value`

`factor` must be > 0.
