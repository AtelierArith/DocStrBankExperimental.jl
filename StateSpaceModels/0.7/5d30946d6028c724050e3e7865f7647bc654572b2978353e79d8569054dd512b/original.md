```
ExperimentalSeasonalNaive(y::Vector{<:Real}, seasonal::Int; S::Int = 10_000)
```

A seasonal naive model where the h step ahead forecast is the mean of the simulation  of S scenarios 

$$
y_{T+h|T} = y_{T + h - m(k+1)} + \varepsilon_t
$$

where m is the seasonal period, k is the integer part of (h-1)/m and $\varepsilon_t$ is a sampled error. 

We call it experimental because so far we could not find a good reference and implementation. If you know something please post it as an issue.
