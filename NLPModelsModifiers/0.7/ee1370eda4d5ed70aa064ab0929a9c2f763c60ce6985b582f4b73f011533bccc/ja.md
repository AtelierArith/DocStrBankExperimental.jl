フィージビリティ残差モデルは、次の形式のNLPModelから作成されます。

$$
\begin{aligned}
       \min_x \quad & f(x) \\
\mathrm{s.t.} \quad & c_L ≤ c(x) ≤ c_U \\
                      & \ell ≤   x  ≤ u,
\end{aligned}
$$

スラック変数$s = c(x)$を作成し、等式制約からNLS問題を定義することによって。結果として得られる問題は、残差関数NLPModelsを持つ境界制約付き非線形最小二乗問題です。$F(x,s) = c(x) - s$：

$$
\begin{aligned}
       \min_{x,s} \quad & \tfrac{1}{2} \|c(x) - s\|^2 \\
\mathrm{s.t.} \quad & \ell ≤ x ≤ u \\
                      & c_L ≤ s ≤ c_U.
\end{aligned}
$$

この問題は`AbstractNLSModel`であることに注意してください。したがって、残差値、ヤコビアン、およびヘッセ行列はNLS APIを通じて明示的に定義されています。スラック変数はSlackModelを使用して作成されます。もし$\ell_i = u_i$であれば、スラック変数は作成されません。特に、$c(x) = 0$の形の等式制約のみがある場合、結果として得られるNLSは単に$\min_x \tfrac{1}{2}\|c(x)\|^2$です。
