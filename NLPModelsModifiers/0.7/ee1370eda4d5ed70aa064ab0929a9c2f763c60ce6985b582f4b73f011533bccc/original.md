A feasibility residual model is created from a NLPModel of the form

$$
\begin{aligned}
       \min_x \quad & f(x) \\
\mathrm{s.t.} \quad & c_L ≤ c(x) ≤ c_U \\
                      & \ell ≤   x  ≤ u,
\end{aligned}
$$

by creating slack variables $s = c(x)$ and defining an NLS problem from the equality constraints. The resulting problem is a bound-constrained nonlinear least-squares problem with residual function NLPModels.$F(x,s) = c(x) - s$:

$$
\begin{aligned}
       \min_{x,s} \quad & \tfrac{1}{2} \|c(x) - s\|^2 \\
\mathrm{s.t.} \quad & \ell ≤ x ≤ u \\
                      & c_L ≤ s ≤ c_U.
\end{aligned}
$$

Notice that this problem is an `AbstractNLSModel`, thus the residual value, Jacobian and Hessian are explicitly defined through the NLS API. The slack variables are created using SlackModel. If $\ell_i = u_i$, no slack variable is created. In particular, if there are only equality constrained of the form $c(x) = 0$, the resulting NLS is simply $\min_x \tfrac{1}{2}\|c(x)\|^2$.
