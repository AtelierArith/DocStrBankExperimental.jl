```
rollmean(u, window::Int64)
```

Returns the rolling mean given a window size `m`

$$
o_k = \frac{\sum_{i=k}^{k+m-1} u_i}{m}
$$

## Rolling functions in ADCME:

  * [`rollmean`](@ref): rolling mean
  * [`rollsum`](@ref): rolling sum
  * [`rollvar`](@ref): rolling variance
  * [`rollstd`](@ref): rolling standard deviation
