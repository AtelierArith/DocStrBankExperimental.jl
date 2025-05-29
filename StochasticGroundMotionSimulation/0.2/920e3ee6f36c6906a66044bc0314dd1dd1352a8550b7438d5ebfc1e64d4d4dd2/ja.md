```
struct SiteAmpBoore2016_760 <: SiteAmplification
```

Vs30 = 760 m/s のための Boore (2016) 増幅関数の実装

# 例

```julia-repl
	f = 5.0
    sa = SiteAmpBoore2016_760()
	Af = sa.amplification(f)
```
