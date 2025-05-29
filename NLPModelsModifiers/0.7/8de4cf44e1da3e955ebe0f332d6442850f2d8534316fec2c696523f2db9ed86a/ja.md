非線形最小二乗問題 $F(x)$ を制約 $F(x) = r$ と目的関数 $\tfrac{1}{2}\|r\|^2$ を持つ非線形最適化問題に変換します。言い換えれば、次のように変換します。

$$
\begin{aligned}
       \min_x \quad & \tfrac{1}{2}\|F(x)\|^2 \\
\mathrm{s.t.} \quad & c_L ≤ c(x) ≤ c_U \\
                      &   ℓ ≤   x  ≤ u
\end{aligned}
$$

を

$$
\begin{aligned}
   \min_{x,r} \quad & \tfrac{1}{2}\|r\|^2 \\
\mathrm{s.t.} \quad & F(x) - r = 0 \\
                      & c_L ≤ c(x) ≤ c_U \\
                      &   ℓ ≤   x  ≤ u
\end{aligned}
$$

に変換します。

最初の問題の方が良い場合は、`nls` モデルはその形式の NLPModel としてすでに機能します。
