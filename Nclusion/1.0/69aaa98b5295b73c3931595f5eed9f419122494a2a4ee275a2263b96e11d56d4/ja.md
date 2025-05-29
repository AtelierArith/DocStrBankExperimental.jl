```
normToProb3!(K,p;float_type=nothing)
```

この関数は、値のベクトルを正規化し、その出力を事前に確保し、インプレースで操作を行います。正規化はベクトルのK番目の要素までのみ行われます。

$$
w_i = \frac{x_i}{\sum_{j=1}^K x_j} \text{ for } i \in \{1,..,K\} 
$$
