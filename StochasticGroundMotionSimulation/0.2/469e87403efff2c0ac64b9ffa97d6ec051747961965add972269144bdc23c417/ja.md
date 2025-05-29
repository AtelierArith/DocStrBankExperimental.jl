```
site_amplification(f::T, amp_model::S; fmin=1e-3, fmax=999.99) where {T<:Real,S<:SiteAmplification}
```

与えられた周波数 `f` に対するサイト増幅（インピーダンス）を計算します。引数 `amp_model` は抽象型 `SiteAmplification` のサブタイプです。

# 例

```julia-repl
	f = 5.0
	# 両方のケースで AlAtik (2021) からの増幅を返します
	Af = site_amplification(f)
    Af = site_amplification(f, SiteAmpAlAtikAbrahamson2021_cy14_760())
    # Boore (2016) の増幅を返します
	Af = site_amplification(f, SiteAmpBoore2016_760())
	# 1.0 を返します
	Af = site_amplification(f, SiteAmpUnit())
```
