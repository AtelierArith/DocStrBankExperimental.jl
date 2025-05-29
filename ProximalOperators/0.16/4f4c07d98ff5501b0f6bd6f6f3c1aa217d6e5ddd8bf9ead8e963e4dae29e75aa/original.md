```
SlicedSeparableSum((f_1, ..., f_k), (J_1, ..., J_k))
```

Return the function

$$
g(x) = \sum_{i=1}^k f_i(x_{J_i}).
$$

```
SlicedSeparableSum(f, (J_1, ..., J_k))
```

Analogous to the previous one, but apply the same function `f` to all slices of the variable `x`:

$$
g(x) = \sum_{i=1}^k f(x_{J_i}).
$$
