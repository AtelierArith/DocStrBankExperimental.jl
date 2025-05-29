```
normToProb3!(p;float_type=nothing)
```

この関数は、出力を事前に確保し、インプレースで操作を行うことによって、値のベクトルを正規化します。

$$
w_i = \frac{x_i}{\sum_{j=1}^n x_j}
$$
