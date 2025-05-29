```
project(::SymplecticMatrices, p, A)
project!(::SymplecticMatrices, Y, p, A)
```

点 $p \in \mathrm{Sp}(2n)$ が与えられたとき、要素 $A \in ℝ^{2n×2n}$ をユークリッド計量に対する接空間 $T_p\mathrm{Sp}(2n)$ に射影します。

つまり、制約付き最適化問題を解く要素 $X \in T_p\operatorname{Sp}(2n)$ を見つけます。

$$
    \operatorname{min}_{X \in ℝ^{2n×2n}} \frac{1}{2}\lVert X - A\rVert^2, \quad
    \text{ただし}\;
    h(X) := X^{\mathrm{T}} J_{2n} p + p^{\mathrm{T}} J_{2n} X = 0,
$$

ここで、$h: ℝ^{2n×2n} → \operatorname{skew}(2n)$ は接空間 $T_p\operatorname{SpSt}(2n, 2k)$ への $X$ の制限を示し、$J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ は [`SymplecticElement`](@ref) を示します。
