```
WienerKernel(; i::Int=0)
WienerKernel{i}()
```

$$
i
$$

回積分されたウィーナー過程カーネル関数。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、$i \in \{-1, 0, 1, 2, 3\}$ の $i$回積分されたウィーナー過程カーネルは次のように定義されます[^SDH]。

$$
k_i(x, x') = \begin{cases}
    \delta(x, x') & \text{if } i=-1,\\
    \min\big(\|x\|_2, \|x'\|_2\big) & \text{if } i=0,\\
    a_{i1}^{-1} \min\big(\|x\|_2, \|x'\|_2\big)^{2i + 1}
    + a_{i2}^{-1} \|x - x'\|_2 r_i\big(\|x\|_2, \|x'\|_2\big) \min\big(\|x\|_2, \|x'\|_2\big)^{i + 1}
    & \text{otherwise},
\end{cases}
$$

ここで、係数 $a$ は次のように与えられます。

$$
a = \begin{bmatrix}
3 & 2 \\
20 & 12 \\
252 & 720
\end{bmatrix}
$$

関数 $r_i$ は次のように定義されます。

$$
\begin{aligned}
r_1(t, t') &= 1,\\
r_2(t, t') &= t + t' - \frac{\min(t, t')}{2},\\
r_3(t, t') &= 5 \max(t, t')^2 + 2 tt' + 3 \min(t, t')^2.
\end{aligned}
$$

[`WhiteKernel`](@ref) は $i = -1$ の場合に回復されます。

[^SDH]: Schober, Duvenaud & Hennig (2014). Probabilistic ODE Solvers with Runge-Kutta Means.
