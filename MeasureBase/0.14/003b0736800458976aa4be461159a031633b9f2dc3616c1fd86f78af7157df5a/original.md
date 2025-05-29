`logdensity_def` is the standard way to define a log-density for a new measure. Note that this definition does not include checking for membership in the support; this is instead checked using `insupport`. `logdensity_def` is a low-level function, and should typically not be called directly. See `logdensityof` for more information and other alternatives.

---

```
logdensity_def(m, x)
```

Compute the log-density of the measure m at the point `x`, relative to `basemeasure(m)`, and assuming `insupport(m, x)`.

---

```
logdensity_def(m1, m2, x)
```

Compute the log-density of `m1` relative to `m2` at the point `x`, assuming `insupport(m1, x)` and `insupport(m2, x)`.
