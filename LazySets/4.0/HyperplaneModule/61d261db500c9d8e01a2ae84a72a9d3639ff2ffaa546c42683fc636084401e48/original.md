# Extended help

```
an_element(H::Hyperplane)
```

### Algorithm

We compute a point on the hyperplane $a⋅x = b$ as follows:

  * We first find a nonzero entry of $a$ in dimension, say, $i$.
  * We set $x[i] = b / a[i]$.
  * We set $x[j] = 0$ for all $j ≠ i$.
