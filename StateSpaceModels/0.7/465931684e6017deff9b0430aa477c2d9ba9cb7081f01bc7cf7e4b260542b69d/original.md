```
SeasonalNaive(y::Vector{<:Real}, seasoanl::Int)
```

A seasonal naive model where the h step ahead forecast is 

$$
y_{T+h|T} = y_{T + h - m(k+1)}
$$

where m is the seasonal period and k is the integer part of (h-1)/m.

# References

  * Hyndman, Rob J., Athanasopoulos, George. "Forecasting: Principles and Practice"
