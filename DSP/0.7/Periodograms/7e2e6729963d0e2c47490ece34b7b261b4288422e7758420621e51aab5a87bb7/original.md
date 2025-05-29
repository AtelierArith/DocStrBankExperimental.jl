```
mt_pgram(s; onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, nw=4, ntapers=iceil(2nw)-1, window=dpss(length(s), nw, ntapers))
mt_pgram(signal::AbstractVector, config::MTConfig)
```

Computes the multitaper periodogram of a signal `s`.

If `window` is not specified, the signal is tapered with `ntapers` discrete prolate spheroidal sequences with time-bandwidth product `nw`. Each sequence is equally weighted; adaptive multitaper is not (yet) supported.

If `window` is specified, each column is applied as a taper. The sum of periodograms is normalized by the total sum of squares of `window`.

Returns a `Periodogram`.

See also [`mt_pgram!`](@ref) and [`MTConfig`](@ref).
