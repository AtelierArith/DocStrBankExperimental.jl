```
project(::SymplecticStiefel, p, A)
project!(::SymplecticStiefel, Y, p, A)
```

点 $p ∈ \mathrm{SpSt}(2n, 2k)$ が与えられたとき、要素 $A ∈ ℝ^{2n×2k}$ を接空間 $T_p\mathrm{SpSt}(2n, 2k)$ に射影します。これは、埋め込み $ℝ^{2n×2k}$ のユークリッド計量に対して行われます。

つまり、制約付き最適化問題を解くことで、要素 $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ を見つけます。

$$
    \displaystyle\operatorname{min}_{X ∈ ℝ^{2n×2k}} \frac{1}{2}||X - A||^2, \quad
    \text{s.t.}\;
    h(X) := X^{\mathrm{T}} J p + p^{\mathrm{T}} J X = 0,
$$

ここで、$h : ℝ^{2n×2k} → \operatorname{skew}(2k)$ は $X$ を接空間 $T_p\mathrm{SpSt}(2n, 2k)$ に制限することを定義します。
