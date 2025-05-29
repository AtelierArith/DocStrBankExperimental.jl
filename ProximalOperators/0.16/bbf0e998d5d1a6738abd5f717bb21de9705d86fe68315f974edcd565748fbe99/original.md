```
CrossEntropy(b)
```

Return the function

$$
f(x) = -\frac{1}{N} \sum_{i = 1}^{N} b_i \log (x_i)+(1-b_i) \log (1-x_i),
$$

where `b` is an array of length `N` such that `0 ≤ b ≤ 1` component-wise.
