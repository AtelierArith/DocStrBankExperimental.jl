```
site_amplification(f::Vector{T}, amp_model::S; fmin=1e-3, fmax=999.99) where {T<:Real,S<:SiteAmplification}
```

Computes the site amplification (impedance) for a given frequency `f`. The argument `amp_model` is a subtype of the abstract type `SiteAmplification`.

# Examples

```julia-repl
	f = 5.0
	# returns the amplification from AlAtik (2021) in both cases
	Af = site_amplification(f)
    Af = site_amplification(f, SiteAmpAlAtikAbrahamson2021_cy14_760())
    # returns the Boore (2016) amplification
	Af = site_amplification(f, SiteAmpBoore2016_760())
	# returns 1.0
	Af = site_amplification(f, SiteAmpUnit())
```
