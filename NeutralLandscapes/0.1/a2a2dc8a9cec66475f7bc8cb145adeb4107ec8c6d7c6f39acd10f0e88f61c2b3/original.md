```
normalize(mats::Vector{M})
```

Normalizes a vector of neutral landscapes `mats` such that all values between 0 and 1. Note that this does not preserve the `rate` parameter for a given `NeutralLandscapeUpdater`, and instead rescales it proportional to the difference between the total maximum and total minimum across all `mats`.
