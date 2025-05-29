```
mix = mixture(signals, amps, [delays::Vector{Int}])
mixes = mixture(signals, amps::Vector{Vector}, [delays::Vector{Vector{Int}}])
```

Mix together signals using amplitudes `amps` and `delays` (`delays` is specified in samples). If `amps` and the optional `delays` are vectors of vectors, then a vector of mixtures is returned. A vector of vectors is converted to a matrix using `M = reduce(hcat, mixes)`.

The returned signals will be shorter than the input signals corresponding to the maximum difference between delays, e.g., if `delays = [-2,0,5]`, the returned mixture will be 7 samples shorter.
