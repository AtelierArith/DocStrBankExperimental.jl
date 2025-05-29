A model whose only inequality constraints are bounds.

Given a model, this type represents a second model in which slack variables are introduced so as to convert linear and nonlinear inequality constraints to equality constraints and bounds. More precisely, if the original model has the form

$$
\begin{aligned}
       \min_x \quad & f(x)\\
\mathrm{s.t.} \quad & c_L ≤ c(x) ≤ c_U,\\
                    &  ℓ  ≤  x   ≤  u,
\end{aligned}
$$

the new model appears to the user as

$$
\begin{aligned}
       \min_X \quad & f(X)\\
\mathrm{s.t.} \quad & g(X) = 0,\\
                    & L ≤ X ≤ U.
\end{aligned}
$$

The unknowns $X = (x, s)$ contain the original variables and slack variables $s$. The latter are such that the new model has the general form

$$
\begin{aligned}
       \min_x \quad & f(x)\\
\mathrm{s.t.} \quad & c(x) - s = 0,\\
                    & c_L ≤ s ≤ c_U,\\
                    &  ℓ  ≤ x ≤ u.
\end{aligned}
$$

although no slack variables are introduced for equality constraints.

The slack variables are implicitly ordered as linear and then nonlinear, and   as `[s(low), s(upp), s(rng)]`, where `low`, `upp` and `rng` represent the indices of the constraints of the form $c_L ≤ c(x) < ∞$, $-∞ < c(x) ≤ c_U$ and $c_L ≤ c(x) ≤ c_U$, respectively.
