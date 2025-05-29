```
PeriodicTransform(f)
```

Transformation that maps the input elementwise onto the unit circle with frequency `f`.

Samples from a GP with a kernel with this transformation applied to the inputs will produce samples with frequency `f`.

# Examples

```jldoctest
julia> f = rand(); t = PeriodicTransform(f); x = rand();

julia> t(x) == [sinpi(2 * f * x), cospi(2 * f * x)]
true
```
