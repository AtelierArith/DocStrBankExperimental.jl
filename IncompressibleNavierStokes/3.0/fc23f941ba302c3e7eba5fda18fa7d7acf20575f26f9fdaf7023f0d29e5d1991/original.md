```julia
struct AdamsBashforthCrankNicolsonMethod{T, M} <: IncompressibleNavierStokes.AbstractODEMethod{T}
```

IMEX AB-CN: Adams-Bashforth for explicit convection (parameters `α₁` and `α₂`) and Crank-Nicolson for implicit diffusion (implicitness `θ`). The method is second order for `θ = 1/2`.

The LU decomposition of the LHS matrix is computed every time the time step changes.

Note that, in contrast to explicit methods, the pressure from previous time steps has an influence on the accuracy of the velocity.

We here require that the time step $\Delta t$ is constant. This methods uses Adams-Bashforth for the convective terms and Crank-Nicolson stepping for the diffusion and body force terms. Given the velocity field $u_0 = u(t_0)$ at a time $t_0$ and its previous value $u_{-1} = u(t_0 - \Delta t)$ at the previous time $t_{-1} = t_0 - \Delta t$, the predicted velocity field $u$ at the time $t = t_0 + \Delta t$ is defined by first computing a tentative velocity:

$$
\begin{split}
\frac{v - u_0}{\Delta t}
& = - (\alpha_0 C(u_0, t_0) + \alpha_{-1} C(u_{-1}, t_{-1})) \\
& + \theta (D u_0 + y_D(t_0)) + (1 - \theta) (D v + y_D(t)) \\
& + \theta f(t_0) + (1 - \theta) f(t) \\
& - (G p_0 + y_G(t_0)),
\end{split}
$$

where $\theta \in [0, 1]$ is the Crank-Nicolson parameter ($\theta = \frac{1}{2}$ for second order convergence), $(\alpha_0, \alpha_{-1}) = \left( \frac{3}{2}, -\frac{1}{2} \right)$ are the Adams-Bashforth coefficients, and $v$ is a tentative velocity yet to be made divergence free. We can group the terms containing $v$ on the left hand side, to obtain

$$
\begin{split}
\left( \frac{1}{\Delta t} I - (1 - \theta) D \right) v
& = \left(\frac{1}{\Delta t} I - \theta D \right) u_0 \\
& - (\alpha_0 C(u_0, t_0) + \alpha_{-1} C(u_{-1}, t_{-1})) \\
& + \theta y_D(t_0) + (1 - \theta) y_D(t) \\
& + \theta f(t_0) + (1 - \theta) f(t) \\
& - (G p_0 + y_G(t_0)).
\end{split}
$$

We can compute $v$ by inverting the positive definite matrix $\left( \frac{1}{\Delta t} I - \theta D \right)$ for the given right hand side using a suitable linear solver. Assuming $\Delta t$ is constant, we can precompute a Cholesky factorization of this matrix before starting time stepping.

We then compute the pressure difference $\Delta p$ by solving

$$
L \Delta p = W \frac{M v + y_M(t)}{\Delta t} - W M (y_G(t) - y_G(t_0)),
$$

after which a divergence free velocity $u$ can be enforced:

$$
u = v - \Delta t (G \Delta p + y_G(t) - y_G(t_0)).
$$

A first order accurate prediction of the corresponding pressure is $p = p_0 + \Delta p$. However, since this pressure is reused in the next time step, we perform an additional pressure solve to avoid accumulating first order errors. The resulting pressure $p$ is then accurate to the same order as $u$.

## Fields

  * `α₁`
  * `α₂`
  * `θ`
  * `p_add_solve`
  * `method_startup`
