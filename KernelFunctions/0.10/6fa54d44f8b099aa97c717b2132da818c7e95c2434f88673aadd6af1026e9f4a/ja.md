```
GibbsKernel(; lengthscale)
```

長さスケール関数 `lengthscale` を持つギブスカーネル。

ギブスカーネルは、二乗指数カーネルの非定常一般化です。長さスケールパラメータ $l$ は位置の関数 $l(x)$ になります。

# 定義

入力 $x, x'$ に対して、長さスケール関数 $l(\cdot)$ を持つギブスカーネルは次のように定義されます。

$$
k(x, x'; l) = \sqrt{\left(\frac{2 l(x) l(x')}{l(x)^2 + l(x')^2}\right)}
\quad \exp{\left(-\frac{(x - x')^2}{l(x)^2 + l(x')^2}\right)}.
$$

定数関数 $l \equiv c$ の場合、長さスケール `c` を持つ [`SqExponentialKernel`](@ref) が得られます。

# 参考文献

Mark N. Gibbs. "Bayesian Gaussian Processes for Regression and Classication." PhD thesis, 1997

Christopher J. Paciorek and Mark J. Schervish. "Nonstationary Covariance Functions for Gaussian Process Regression". NeurIPS, 2003

Sami Remes, Markus Heinonen, Samuel Kaski. "Non-Stationary Spectral Kernels". arXiV:1705.08736, 2017

Sami Remes, Markus Heinonen, Samuel Kaski. "Neural Non-Stationary Spectral Kernel". arXiv:1811.10978, 2018
