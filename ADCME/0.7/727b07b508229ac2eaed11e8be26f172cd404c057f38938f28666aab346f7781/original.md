```
rollstd(u, window::Int64)
```

Returns the rolling standard deviation given a window size `m`

$$
o_k = \sqrt{\frac{\sum_{i=k}^{k+m-1} (u_i - m_i)^2}{m-1}}
$$

Here $m_i$ is the rolling mean computed using [`rollmean`](@ref)

## Rolling functions in ADCME:

  * [`rollmean`](@ref): rolling mean
  * [`rollsum`](@ref): rolling sum
  * [`rollvar`](@ref): rolling variance
  * [`rollstd`](@ref): rolling standard deviation
