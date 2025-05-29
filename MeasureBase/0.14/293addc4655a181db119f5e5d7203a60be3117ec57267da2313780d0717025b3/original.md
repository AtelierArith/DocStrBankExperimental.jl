```
massof(m)
```

Get the *mass* of a measure - that is, integrate the measure over its support.

`massof` 

---

```
massof(m, dom)
```

Integrate the measure `m` over the "domain" `dom`. Note that domains are not defined universally, but may be specific to a given measure. If `m` is `<:AbstractMeasure`, users can also write `m(dom)`. For new measures, users should *not* add new "call" methods, but instead extend `MeasureBase.massof`.

For example, for many univariate measures `m` with `rootmeasure(m) == LebesgueBase()`, users can call `massof(m, a_b)` where `a_b::IntervalSets.Interval`.

`massof` often returns a `Real`. But in many cases we may only know the mass is finite, or we may know nothing at all about it. For these cases, it will return `UnknownFiniteMass` or `UnknownMass`, respectively. When no `massof` method exists, it defaults to `UnknownMass`.
