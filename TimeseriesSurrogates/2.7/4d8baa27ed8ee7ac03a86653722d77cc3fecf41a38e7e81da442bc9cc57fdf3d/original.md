```
BlockShuffle(n::Int; shift = false)
```

A block shuffle surrogate constructed by dividing the time series into `n` blocks of roughly equal width at random indices (end blocks are wrapped around to the start of the time series).

If `shift` is `true`, then the input signal is circularly shifted by a  random number of steps prior to picking blocks.

Block shuffle surrogates roughly preserve short-range temporal properties in the time series (e.g. correlations at lags less than the block length), but break any long-term dynamical information (e.g. correlations beyond the block length).

Hence, these surrogates can be used to test any null hypothesis aimed at comparing short-range dynamical properties versus long-range dynamical properties of the signal.
