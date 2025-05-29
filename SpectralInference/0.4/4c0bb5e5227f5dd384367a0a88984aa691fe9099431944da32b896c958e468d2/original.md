```
empiricalMI(a::AbstractVector{<:Float}, b::AbstractVector{<:Float}[, nbins=50, normalize=false])
```

computes empirical MI from identity of $H(a) + H(b) - H(a,b)$. where $H := -sum(p(x)*log(p(x))) + log(Δ)$ the $+ log(Δ)$ corresponds to the log binwidth and unbiases the entropy estimate from binwidth choice. estimates are roughly stable from $32$ ($32^2 ≈ 1000$ total bins) to size of sample. going from a small undersestimate to a small overestimate across that range. We recommend choosing the `sqrt(mean(1000, samplesize))` for `nbins` argument, or taking a few estimates across that range and averaging.

Args:

  * a, vecter of length N
  * b, AbstractVector of length N
  * nbins, number of bins per side, use 1000 < nbins^2 < length(a) for best results
  * base, base unit of MI (defaults to nats with base=ℯ)
  * normalize, bool, whether to normalize with mi / mean(ha, hb)

Returns:

  * MI
