```
SlicedSeparableSum((f_1, ..., f_k), (J_1, ..., J_k))
```

関数を返します

$$
g(x) = \sum_{i=1}^k f_i(x_{J_i}).
$$

```
SlicedSeparableSum(f, (J_1, ..., J_k))
```

前のものと類似していますが、変数 `x` のすべてのスライスに同じ関数 `f` を適用します：

$$
g(x) = \sum_{i=1}^k f(x_{J_i}).
$$
