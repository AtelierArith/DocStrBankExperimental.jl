```
AmplMPECModel
```

Smooth reformulation for an Ampl model with complementarity constraints.

The nonlinear program

$$
\begin{aligned}
       min_x  \quad &  f(x)\\
\mathrm{s.t.} \quad &  c_L ≤ c(x) ≤ c_U,\\
                    &  g_L ≤ g(x) ⟂ x ≥ x_L,
\end{aligned}
$$

is reformulated as

$$
\begin{aligned}
       min_x  \quad &  f(x)\\
\mathrm{s.t.} \quad &  c_L ≤ c(x) ≤ c_U,\\
                    &  g_L ≤ g(x)  \\
                    &  x_L ≤ x \\
                    &  Diag(g(x)) x ≤ 0
\end{aligned}
$$

Return the original model if it does not have complementarity constraints.
