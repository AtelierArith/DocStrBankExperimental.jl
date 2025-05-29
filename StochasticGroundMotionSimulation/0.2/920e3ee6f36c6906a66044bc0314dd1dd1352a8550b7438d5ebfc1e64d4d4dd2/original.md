```
struct SiteAmpBoore2016_760 <: SiteAmplification
```

Implementation of the Boore (2016) amplification function for Vs30 = 760 m/s

# Examples

```julia-repl
	f = 5.0
    sa = SiteAmpBoore2016_760()
	Af = sa.amplification(f)
```
