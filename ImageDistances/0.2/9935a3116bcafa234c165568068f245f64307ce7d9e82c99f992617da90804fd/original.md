```
NCC <: Metric
ncc(x, y)
```

Normalized Cross-correlation(ncc) is calculated by `dot(mean(x),mean(y))/(norm(mean(x))*norm(mean(y)))`

$$
\frac{<\bar{x}, \bar{y}>}{||\bar{x}||*||\bar{y}||}
$$

!!! info
    NCC isn't a Metric because `ncc(x, x) == 1.0`

