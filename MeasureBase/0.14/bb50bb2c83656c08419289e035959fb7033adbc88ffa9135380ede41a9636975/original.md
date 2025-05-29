```
isnormalized(m::AbstractMeasure)
```

Checks whether the measure m is normalized, that is, whether `massof(m) == 1`. 

For convenience, we also provide a method on non-measures that only depends on `norm`.
