```
hampel(x; spread=mad(x), threshold=2)
```

Identify outliers using the Hampel criterion.

Given vector `x`, identify elements xₖ such that

$$
|xₖ - m| > t S,
$$

where $m$ is the median of the elements, the dispersion scale $S$ is provided by the function `spread`, and the parameter $t$ is given by `threshold`. The return value is a `Bool` vector.

By default, `spread` is `mad` and `threshold` is 2.
