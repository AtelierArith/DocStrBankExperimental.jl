# Extended help

```
center(P::HParallelotope)
```

### Algorithm

Let $P$ be a parallelotope with base vertex $q$ and list of extremal vertices with respect to $q$ given by the set $\{v_i\}$ for $i = 1, …, n$. Then the center is located at

$$
    c = q + ∑_{i=1}^n \frac{v_i - q}{2} = q (1 - \frac{2}) + \frac{s}{2},
$$

where $s := ∑_{i=1}^n v_i$ is the sum of extremal vertices.
