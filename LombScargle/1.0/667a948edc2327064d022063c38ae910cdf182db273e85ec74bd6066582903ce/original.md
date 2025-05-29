```
findmaxfreq(p::Periodogram, [interval::AbstractVector{Real}], threshold::Real=findmaxpower(p))
```

Return the array of frequencies with the highest power in the periodogram `p`. If a scalar real argument `threshold` is provided, return the frequencies with power larger than or equal to `threshold`.  If you want to limit the search to a narrower frequency range, pass as second argument a vector with the extrema of the interval.
