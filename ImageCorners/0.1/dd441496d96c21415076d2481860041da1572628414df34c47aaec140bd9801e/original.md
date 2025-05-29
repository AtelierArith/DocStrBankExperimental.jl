```
Percentile(x)
```

Indicate that `x` should be interpreted as a [percentile](https://en.wikipedia.org/wiki/Percentile) rather than an absolute value. For example,

  * `canny(img, 1.4, (80, 20))` uses absolute thresholds on the edge magnitude image
  * `canny(img, 1.4, (Percentile(80), Percentile(20)))` uses percentiles of the edge magnitude image as threshold
