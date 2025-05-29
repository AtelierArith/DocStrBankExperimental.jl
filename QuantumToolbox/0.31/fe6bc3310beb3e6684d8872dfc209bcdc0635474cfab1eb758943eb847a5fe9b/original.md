```
steadystate_fourier(
    H_0::QuantumObject,
    H_p::QuantumObject,
    H_m::QuantumObject,
    ωd::Number,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    n_max::Integer = 2,
    tol::R = 1e-8,
    solver::FSolver = SteadyStateLinearSolver(),
    kwargs...,
)
```

Calculates the steady state of a periodically driven system. Here `H_0` is the Hamiltonian or the Liouvillian of the undriven system. Considering a monochromatic drive at frequency $\omega_d$, we divide it into two parts, `H_p` and `H_m`, where `H_p` oscillates as $e^{i \omega t}$ and `H_m` oscillates as $e^{-i \omega t}$. There are two solvers available for this function:

  * `SteadyStateLinearSolver`: Solves the linear system of equations.
  * `SSFloquetEffectiveLiouvillian`: Solves the effective Liouvillian.

For both cases, `n_max` is the number of Fourier components to consider, and `tol` is the tolerance for the solver.

In the case of `SteadyStateLinearSolver`, the full linear system is solved at once:

$$
( \mathcal{L}_0 - i n \omega_d ) \hat{\rho}_n + \mathcal{L}_1 \hat{\rho}_{n-1} + \mathcal{L}_{-1} \hat{\rho}_{n+1} = 0
$$

This is a tridiagonal linear system of the form

$$
\mathbf{A} \cdot \mathbf{b} = 0
$$

where

$$
\mathbf{A} = \begin{pmatrix}
\mathcal{L}_0 - i (-n_{\textrm{max}}) \omega_{\textrm{d}} & \mathcal{L}_{-1} & 0 & \cdots & 0 \\
\mathcal{L}_1 & \mathcal{L}_0 - i (-n_{\textrm{max}}+1) \omega_{\textrm{d}} & \mathcal{L}_{-1} & \cdots & 0 \\
0 & \mathcal{L}_1 & \mathcal{L}_0 - i (-n_{\textrm{max}}+2) \omega_{\textrm{d}} & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & \mathcal{L}_0 - i n_{\textrm{max}} \omega_{\textrm{d}}
\end{pmatrix}
$$

and

$$
\mathbf{b} = \begin{pmatrix}
\hat{\rho}_{-n_{\textrm{max}}} \\
\hat{\rho}_{-n_{\textrm{max}}+1} \\
\vdots \\
\hat{\rho}_{0} \\
\vdots \\
\hat{\rho}_{n_{\textrm{max}}-1} \\
\hat{\rho}_{n_{\textrm{max}}}
\end{pmatrix}
$$

This will allow to simultaneously obtain all the $\hat{\rho}_n$.

In the case of `SSFloquetEffectiveLiouvillian`, instead, the effective Liouvillian is calculated using the matrix continued fraction method.

!!! note "different return"
    The two solvers returns different objects. The `SteadyStateLinearSolver` returns a list of [`QuantumObject`](@ref), containing the density matrices for each Fourier component ($\hat{\rho}_{-n}$, with $n$ from $0$ to $n_\textrm{max}$), while the `SSFloquetEffectiveLiouvillian` returns only $\hat{\rho}_0$.


!!! note
    `steadystate_floquet` is a synonym of `steadystate_fourier`.


## Arguments

  * `H_0::QuantumObject`: The Hamiltonian or the Liouvillian of the undriven system.
  * `H_p::QuantumObject`: The Hamiltonian or the Liouvillian of the part of the drive that oscillates as $e^{i \omega t}$.
  * `H_m::QuantumObject`: The Hamiltonian or the Liouvillian of the part of the drive that oscillates as $e^{-i \omega t}$.
  * `ωd::Number`: The frequency of the drive.
  * `c_ops::Union{Nothing,AbstractVector} = nothing`: The optional collapse operators.
  * `n_max::Integer = 2`: The number of Fourier components to consider.
  * `tol::R = 1e-8`: The tolerance for the solver.
  * `solver::FSolver = SteadyStateLinearSolver`: The solver to use.
  * `kwargs...`: Additional keyword arguments to be passed to the solver.
