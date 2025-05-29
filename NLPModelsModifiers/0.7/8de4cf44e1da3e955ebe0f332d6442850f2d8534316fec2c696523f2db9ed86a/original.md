Converts a nonlinear least-squares problem with residual $F(x)$ to a nonlinear optimization problem with constraints $F(x) = r$ and objective $\tfrac{1}{2}\|r\|^2$. In other words, converts

$$
\begin{aligned}
       \min_x \quad & \tfrac{1}{2}\|F(x)\|^2 \\
\mathrm{s.t.} \quad & c_L ≤ c(x) ≤ c_U \\
                      &   ℓ ≤   x  ≤ u
\end{aligned}
$$

to

$$
\begin{aligned}
   \min_{x,r} \quad & \tfrac{1}{2}\|r\|^2 \\
\mathrm{s.t.} \quad & F(x) - r = 0 \\
                      & c_L ≤ c(x) ≤ c_U \\
                      &   ℓ ≤   x  ≤ u
\end{aligned}
$$

If you rather have the first problem, the `nls` model already works as an NLPModel of that format.
