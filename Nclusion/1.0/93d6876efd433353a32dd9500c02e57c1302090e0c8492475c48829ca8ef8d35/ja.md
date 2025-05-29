```
norm_weights3(p;float_type=nothing)
```

この関数は、出力を事前に確保することによって、対数スケールでの値のベクトルを正規化します。

$$
π_i=exp(x_i− logsumexp(x)) where logsumexp(x)=b+log∑_{j=1}^n exp(x_j−b)
π_i in [0,1]
$$
