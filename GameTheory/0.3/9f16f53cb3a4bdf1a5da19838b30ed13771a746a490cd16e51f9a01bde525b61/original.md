```
FictitiousPlay(g[, gain=DecreasingGain()])
```

Construct a `FictitiousPlay` instance from `NormalFormGame`.

# Arguments

  * `g::NormalFormGame` : `NormalFormGame` instance.
  * `gain::AbstractGain` : Argument to specify the gain or step size; `DecreasingGain()` or `ConstantGain(size)`.

# Returns

  * `::FictitiousPlay` : The fictitious play model.
