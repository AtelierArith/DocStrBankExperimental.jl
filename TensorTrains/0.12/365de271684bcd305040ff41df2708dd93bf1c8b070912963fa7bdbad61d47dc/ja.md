```
marginals(A::AbstractTensorTrain; l, r)
```

各サイトでの周辺分布 $p(x^l)$ を計算します

### オプション引数

  * `l = accumulate_L(A)[1]`, `r = accumulate_R(A)[1]` 事前に計算された部分正規化
