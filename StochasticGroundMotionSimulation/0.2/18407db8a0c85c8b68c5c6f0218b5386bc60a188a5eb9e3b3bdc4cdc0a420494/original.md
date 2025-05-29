```
struct SiteAmpAlAtikAbrahamson2021_ask14_620 <: SiteAmplification
```

Implementation of the Al Atik & Abrahamson (2021) amplification function for the Abrahamson *et al.* (2014) GMM, for Vs30 = 620 m/s

# Examples

```julia-repl
	f = 5.0
    sa = SiteAmpAlAtikAbrahamson2021_ask14_620()
	Af = sa.amplification(f)
```
