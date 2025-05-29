```julia
SplitData(location, measurement, ratioₜ, seed)

```

Split location and acoustic measurement data into training and validation dataset.

  * `location`: measurement locations
  * `measurement`: coresponding acoustic measurements
  * `ratioₜ`: training data split ratio
  * set `seed` to `true` to seed the random order generation in data split
