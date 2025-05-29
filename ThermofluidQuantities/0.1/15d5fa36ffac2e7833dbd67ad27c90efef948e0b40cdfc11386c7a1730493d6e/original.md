```
value(a::PhysicalQuantity,units::Unitful.Units)
```

Return the numerical value of `a`, converted to units `units`. The form of `units` must be of `Unitful` form, e.g. `u"Pa"` and must be dimensionally compatible with `a`
