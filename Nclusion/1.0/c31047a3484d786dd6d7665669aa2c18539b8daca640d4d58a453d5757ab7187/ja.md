```
norm_weights(p)
```

この関数は、対数スケールで値のベクトルを正規化します。

$$
π_i=exp(x_i− logsumexp(x)) \text{ where } logsumexp(x)=b+log∑_{j=1}^n exp(x_j−b)
π_i \in [0,1]
$$
