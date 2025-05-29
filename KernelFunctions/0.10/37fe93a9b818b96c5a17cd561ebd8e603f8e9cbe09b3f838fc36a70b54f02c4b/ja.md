```
PiecewisePolynomialKernel(; dim::Int, degree::Int=0, metric=Euclidean())
PiecewisePolynomialKernel{degree}(; dim::Int, metric=Euclidean())
```

次のメトリックに関して、次元 `dim` の入力に対する次数 `degree` の区分多項式カーネル。

# 定義

次元 $m$ の入力 $x, x'$ とメトリック $d(\cdot, \cdot)$ に対して、次数 $v \in \{0,1,2,3\}$ の区分多項式カーネルは次のように定義されます。

$$
k(x, x'; v) = \max(1 - d(x, x'), 0)^{\alpha(v,m)} f_{v,m}(d(x, x')),
$$

ここで、$\alpha(v, m) = \lfloor \frac{m}{2}\rfloor + 2v + 1$ であり、$f_{v,m}$ は次のように与えられる次数 $v$ の多項式です。

$$
\begin{aligned}
f_{0,m}(r) &= 1, \\
f_{1,m}(r) &= 1 + (j + 1) r, \\
f_{2,m}(r) &= 1 + (j + 2) r + \big((j^2 + 4j + 3) / 3\big) r^2, \\
f_{3,m}(r) &= 1 + (j + 3) r + \big((6 j^2 + 36j + 45) / 15\big) r^2 + \big((j^3 + 9 j^2 + 23j + 15) / 15\big) r^3,
\end{aligned}
$$

ここで、$j = \lfloor \frac{m}{2}\rfloor + v + 1$ です。デフォルトでは、$d$ はユークリッドメトリック $d(x, x') = \|x - x'\|_2$ です。

このカーネルは $2v$ 回連続微分可能であり、対応するガウス過程はしたがって $v$ 回平均二乗微分可能です。
