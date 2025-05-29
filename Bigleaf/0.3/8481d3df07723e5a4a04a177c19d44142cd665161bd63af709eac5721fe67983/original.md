```
moving_average(vs,n; nmin = n ÷ 2)
```

Compute the moving average over a vector allowing for missings.

# Arguments

  * vs: numeric vector to average over
  * n: window size: number of items to average
  * nmin: minimum number of non-missing records

Values outside the edges are assumed missing.    

If the number of non-missing records within a window is smaller than nmin then the averaged value is assumed missing. This avoids average at edges of  periods with many missings to be very sensitive to the edge values.
