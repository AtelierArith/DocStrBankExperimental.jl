```
PeriodicKernel(; r::AbstractVector=ones(Float64, 1))
```

パラメータ `r` を持つ周期カーネル。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、パラメータ $r_i > 0$ を持つ周期カーネルは次のように定義されます[^DM]。

$$
k(x, x'; r) = \exp\bigg(- \frac{1}{2} \sum_{i=1}^d \bigg(\frac{\sin\big(\pi(x_i - x'_i)\big)}{r_i}\bigg)^2\bigg).
$$

[^DM]: D. J. C. MacKay (1998). Introduction to Gaussian Processes.
