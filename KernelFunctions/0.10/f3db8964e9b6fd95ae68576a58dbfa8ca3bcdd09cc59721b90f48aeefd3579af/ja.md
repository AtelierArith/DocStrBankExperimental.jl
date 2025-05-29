```
IndependentMOKernel(k::Kernel)
```

カーネル `k` を持つ複数の独立した出力のためのカーネルです。

# 定義

入力 $x, x'$ と出力次元 $p, p'$ に対して、各カーネル $k$ を持つ独立出力のためのカーネル $\widetilde{k}$ は次のように定義されます。

$$
\widetilde{k}\big((x, p), (x', p')\big) = \begin{cases}
    k(x, x') & \text{if } p = p', \\
    0 & \text{otherwise}.
\end{cases}
$$

数学的には、次のように定義される行列値カーネルと同等です。

$$
\widetilde{K}(x, x') = \mathrm{diag}\big(k(x, x'), \ldots, k(x, x')\big) \in \mathbb{R}^{m \times m},
$$

ここで $m$ は出力の数です。
