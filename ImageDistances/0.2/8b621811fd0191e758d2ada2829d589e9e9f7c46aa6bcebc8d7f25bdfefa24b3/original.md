```
ZNCC <: PreMetric
zncc(x, y)
```

Zero-mean Normalized Cross-correlation(ZNCC) is calculated by `dot(x,y)/(norm(x)*norm(y))`:

$$
\frac{<\bar{x}, \bar{y}>}{||\bar{x}||*||\bar{y}||}
$$

where `x`/`y` are zero-meaned, i.e., `x := x - mean(x)`.

!!! info
    ZNCC isn't a `Metric` because `zncc(x, x) == 1.0`. ZNCC might output `NaN` if any of the input array is all-zero.


# References

[1] Nakhmani, Arie, and Allen Tannenbaum. "A new distance measure based on generalized image normalized cross-correlation for robust video tracking and image recognition." *Pattern recognition letters* 34.3 (2013): 315-321.
