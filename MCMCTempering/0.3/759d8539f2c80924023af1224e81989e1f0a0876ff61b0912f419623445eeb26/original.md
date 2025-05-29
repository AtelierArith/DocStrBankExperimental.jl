```
RandomSwap <: AbstractSwapStrategy
```

This strategy randomly shuffles all the chain indices to produce `floor(numptemps(sampler)/2)` pairs of random (not necessarily neighbouring) chain indices to attempt to swap
