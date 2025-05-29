```
CosineKernel(; metric=Euclidean())
```

Cosine kernel with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the cosine kernel is defined as

$$
k(x, x') = \cos(\pi d(x, x')).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.
