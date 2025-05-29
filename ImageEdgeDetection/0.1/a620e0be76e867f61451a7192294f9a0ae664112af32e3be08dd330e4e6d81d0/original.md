```
Percentile(x)
```

Indicate that `x` should be interpreted as a [percentile](https://en.wikipedia.org/wiki/Percentile) rather than an absolute value. For example,

  * `detect_edges(img, Canny(high = 80, low = 20))` uses absolute thresholds on the edge magnitudes
  * `detect_edges(img, Canny(high = Percentile(80), low = Percentile(20)))` uses percentiles of the edge magnitude image as threshold
