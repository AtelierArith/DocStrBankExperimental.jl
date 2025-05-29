```
αscheme(M::Union{SparseTensor, SparseMatrixCSC}, 
    C::Union{SparseTensor, SparseMatrixCSC}, 
    K::Union{SparseTensor, SparseMatrixCSC}, 
    Force::Union{Array{Float64}, PyObject}, 
    d0::Union{Array{Float64, 1}, PyObject}, 
    v0::Union{Array{Float64, 1}, PyObject}, 
    a0::Union{Array{Float64, 1}, PyObject}, 
    Δt::Array{Float64}; 
    solve::Union{Missing, Function} = missing,
    extsolve::Union{Missing, Function} = missing, 
    ρ::Float64 = 1.0)
```

Generalized α-scheme.  $M u_{tt} + C u_{t} + K u = F$

`Force` must be an array of size `n`×`p`, where `d0`, `v0`, and `a0` have a size `p` `Δt` is an array (variable time step). 

The generalized α scheme solves the equation by the time stepping

$$
\begin{aligned}
\bf d_{n+1} &= \bf d_n + h\bf v_n + h^2 \left(\left(\frac{1}{2}-\beta_2 \right)\bf a_n + \beta_2 \bf a_{n+1}  \right)\\
\bf v_{n+1} &= \bf v_n + h((1-\gamma_2)\bf a_n + \gamma_2 \bf a_{n+1})\\
\bf F(t_{n+1-\alpha_{f_2}}) &= M \bf a _{n+1-\alpha_{m_2}} + C \bf v_{n+1-\alpha_{f_2}} + K \bf{d}_{n+1-\alpha_{f_2}}
\end{aligned}
$$

where 

$$
\begin{aligned}
\bf d_{n+1-\alpha_{f_2}} &= (1-\alpha_{f_2})\bf d_{n+1} + \alpha_{f_2} \bf d_n\\
\bf v_{n+1-\alpha_{f_2}} &= (1-\alpha_{f_2}) \bf v_{n+1} + \alpha_{f_2} \bf v_n \\
\bf a_{n+1-\alpha_{m_2} } &= (1-\alpha_{m_2}) \bf a_{n+1} + \alpha_{m_2} \bf a_n\\
t_{n+1-\alpha_{f_2}} & = (1-\alpha_{f_2}) t_{n+1 + \alpha_{f_2}} + \alpha_{f_2}t_n
\end{aligned}
$$

Here the parameters are computed using 

$$
\begin{aligned}
\gamma_2 &= \frac{1}{2} - \alpha_{m_2} + \alpha_{f_2}\\
\beta_2 &= \frac{1}{4} (1-\alpha_{m_2}+\alpha_{f_2})^2 \\
\alpha_{m_2} &= \frac{2\rho_\infty-1}{\rho_\infty+1}\\
\alpha_{f_2} &= \frac{\rho_\infty}{\rho_\infty+1}
\end{aligned}
$$

∘ `solve`: users can provide a solver function, `solve(A, rhs)` for solving `Ax = rhs` ∘ `extsolve`: similar to `solve`, but the signature has the form 

```julia
extsolve(A, rhs, i)
```

This provides the users with more control, e.g., (time-dependent) Dirichlet boundary conditions.  See [Generalized α Scheme](https://kailaix.github.io/ADCME.jl/dev/alphascheme/) for details.

!!! note
    In the case $u$ has a nonzero essential boundary condition $u_b$, we let $\tilde u=u-u_b$, then  $M \tilde u_{tt} + C \tilde u_t + K u = F - K u_b - C \dot u_b$

