```
kurtosis(::ContinuousHistogram [, excess = true ])
```

[Pearson (`excess`) kurtosis](https://en.wikipedia.org/wiki/Kurtosis?oldformat=true#Pearson_moments) of a [`ContinuousHistogram`](@ref).

!!! note
    For comparison purposes, this `kurtosis` definition, with `excess == true`, applied to a  Gaussian distribution yields `0`. If `excess == false`, then the `kurtosis` for a Gaussian is 3.

