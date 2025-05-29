```
 (graph,crefs)=graph_ps(a; input=:A,
                      B_base=:B, C_base=:C, P_base=:P)
```

モノミアル基底係数を持つパターソン–ストックマイヤー手法のグラフを生成します。より正確には、これは多項式の評価に対応します。

```
p(s) = a[1] + a[2]*s + ... + a[n]*s^(n-1).
```

このコードは、以下の文献の2番目の説明に従っています。

**参考文献**

1. M. Paterson and L. Stockmeyer. "On the number of nonscalar multiplications necessary to evaluate polynomials". SIAM Journal on Scientific Computing, 2(1):60-66, 1973. DOI: [10.1137/0202007](https://doi.org/10.1137/0202007)
2. M. Fasi. "Optimality of the Paterson–Stockmeyer method for evaluating matrix polynomials and rational matrix functions". Linear Algebra and its Applications, 574, 2019. DOI: [10.1016/j.laa.2019.04.001](https://doi.org/10.1016/j.laa.2019.04.001)
