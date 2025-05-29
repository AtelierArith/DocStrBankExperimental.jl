```
struct SiteAmpAlAtikAbrahamson2021_ask14_620 <: SiteAmplification
```

Al Atik & Abrahamson (2021) の増幅関数の実装で、Abrahamson *et al.* (2014) GMM のため、Vs30 = 620 m/s

# 例

```julia-repl
	f = 5.0
    sa = SiteAmpAlAtikAbrahamson2021_ask14_620()
	Af = sa.amplification(f)
```
