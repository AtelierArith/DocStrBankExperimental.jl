```
rollsum(u, window::Int64)
```

Returns the rolling sum given a window size `m`

$$
o_k = \sum_{i=k}^{k+m-1} u_i
$$

## Rolling functions in ADCME:

  * [`rollmean`](@ref): rolling mean
  * [`rollsum`](@ref): rolling sum
  * [`rollvar`](@ref): rolling variance
  * [`rollstd`](@ref): rolling standard deviation
