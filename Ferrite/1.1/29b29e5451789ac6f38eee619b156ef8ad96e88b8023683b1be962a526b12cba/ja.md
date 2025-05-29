```
getdetJdV(fe_v::AbstractValues, q_point::Int)
```

与えられた数値積分点に対するヤコビアンの行列式と数値積分点の重みの積を返します: $\det(J(\mathbf{x})) w_q$。

この値は、有限要素セルまたはファセット上で関数を積分する際に通常使用されます。

$$
\int\limits_\Omega f(\mathbf{x}) d \Omega \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) \det(J(\mathbf{x})) w_q
$$

$\int\limits_\Gamma f(\mathbf{x}) d \Gamma \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) \det(J(\mathbf{x})) w_q$
