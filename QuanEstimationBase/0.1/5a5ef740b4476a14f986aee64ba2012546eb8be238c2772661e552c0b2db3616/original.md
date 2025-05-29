```
ode(tspan::AbstractVector, ρ0::AbstractMatrix, H0::AbstractVector, dH::AbstractVector; decay::Union{AbstractVector, Nothing}=nothing, Hc::Union{AbstractVector, Nothing}=nothing, ctrl::Union{AbstractVector, Nothing}=nothing)
```

The dynamics of a density matrix is of the form  $\partial_t\rho=-i[H,\rho]+\sum_i \gamma_i\left(\Gamma_i\rho\Gamma^{\dagger}_i-\frac{1}{2}\left\{\rho,\Gamma^{\dagger}_i \Gamma_i \right\}\right)$, where $\rho$ is the evolved density matrix, $H$ is the Hamiltonian of the system, $\Gamma_i$ and $\gamma_i$ are the $i\mathrm{th}$ decay operator and the corresponding decay rate.

  * `tspan`: Time length for the evolution.
  * `ρ0`: Initial state (density matrix).
  * `H0`: Free Hamiltonian.
  * `dH`: Derivatives of the free Hamiltonian with respect to the unknown parameters to be estimated. For example, dH[0] is the derivative vector on the first parameter.
  * `decay`: Decay operators and the corresponding decay rates. Its input rule is decay=[[$\Gamma_1$, $\gamma_1$], [$\Gamma_2$, $\gamma_2$],...], where $\Gamma_1$ $(\Gamma_2)$ represents the decay operator and $\gamma_1$ $(\gamma_2)$ is the corresponding decay rate.
  * `Hc`: Control Hamiltonians.
  * `ctrl`: Control coefficients.
