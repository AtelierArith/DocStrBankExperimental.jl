```
ReservoirSample(k::Int, T::Type = Float64)
```

Create a sample without replacement of size `k`.  After running through `n` observations, the probability of an observation being in the sample is `1 / n`.

# Example

```
fit!(ReservoirSample(100, Int), 1:1000)
```
