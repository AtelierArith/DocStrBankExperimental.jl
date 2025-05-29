```
sampleITE(g, doT)
sampleITE(g, doT; samplesPerPosterior=10)
```

Estimate Individual Treatment Effect with CausalGPSLC model

Params:

  * `g::`[`GPSLCObject`](@ref): Contains data and hyperparameters
  * `doT`: The requested intervention (e.g. set all treatments to 1.0)
  * `samplesPerPosterior`: How many ITE samples to draw per posterior sample in `g`.

Returns:

`ITEsamples`: `n x m` matrix where `n` is the number of individuals, and `m` is the number of samples.
