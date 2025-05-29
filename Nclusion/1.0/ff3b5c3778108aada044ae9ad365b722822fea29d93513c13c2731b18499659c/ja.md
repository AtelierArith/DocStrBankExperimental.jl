```
norm_weights3!(K,p;float_type=nothing)
```

この関数は、出力を事前に確保し、インプレースで操作を行うことによって、対数スケールでの値のベクトルを正規化します。正規化はベクトルのK番目の要素までのみ行われます。

$$
π_i=exp(x_i− logsumexp(x)) \text{ where } logsumexp(x)=b+log∑_{j=1}^K exp(x_j−b)
\text{ for } π_i in [0,1] \text{and} i in {1,..,K}
$$
