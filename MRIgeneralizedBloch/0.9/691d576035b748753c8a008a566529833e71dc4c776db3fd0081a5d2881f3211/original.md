```
hamiltonian_linear(ω1, B1, ω0, T, m0s, R1f, R2f, Rx, R1s, R2s[, dR2sdT2s, dR2sdB1, grad_type])
```

Calculate the hamiltonian of the linear approximation of the generalized Bloch model.

If no gradient is supplied, it returns a 6x6 (static) matrix with the dimensions (in this order) `[xf, yf, zf, xs, zs, 1]`; the attached 1 is a mathematical trick to allow for $T_1$ relaxation to a non-zero thermal equilibrium. If a gradient is supplied, it returns a 11x11 (static) matrix with the dimensions (in this order) `[xf, yf, zf, xs, zs, dxf/dθ, dyf/dθ, dzf/dθ, dxs/dθ, dzs/dθ,  1]`, where `θ` is the parameter specified by `grad_type`

# Arguments

  * `ω1::Real`: Rabi frequency in rad/s (rotation about the y-axis)
  * `B1::Real`: Normalized transmit B1 field, i.e. B1 = 1 corresponds to a well-calibrated B1 field
  * `ω0::Real`: Larmor (or off-resonance) frequency in rad/s (rotation about the z-axis)
  * `T::Real`: Time in seconds; this can, e.g., be the RF-pulse duration, or the time of free precession with `ω1=0`
  * `m0s::Real`: Fractional size of the semi-solid pool; should be in range of 0 to 1
  * `R1f::Real`: Longitudinal relaxation rate of the free pool in 1/seconds
  * `R2f::Real`: Transversal relaxation rate of the free pool in 1/seconds
  * `Rx::Real`: Exchange rate between the two spin pools in 1/seconds
  * `R1s::Real`: Longitudinal relaxation rate of the semi-solid pool in 1/seconds
  * `R2s::Real`: Transversal relaxation rate of the semi-solid pool in 1/seconds; this number can be calculated with the first function returned by [`precompute_R2sl`](@ref) to implement the linear approximation described in the generalized Bloch paper

Optional:

  * `dR2sdT2s::Real`: Derivative of linearized R2sl wrt. the actual T2s; only required if `grad_type = grad_T2s()`; this number can be calculated with the second function returned by [`precompute_R2sl`](@ref)
  * `dR2sdB1::Real`: Derivative of linearized R2sl wrt. B1; only required if `grad_type = grad_B1()`; this number can be calculated with the third function returned by [`precompute_R2sl`](@ref)
  * `grad_type::grad_param`: `grad_m0s()`, `grad_R1f()`, `grad_R1s()`, `grad_R2f()`, `grad_Rx()`, `grad_T2s()`, `grad_ω0()`, or `grad_B1()`; create one hamiltonian for each desired gradient

# Examples

```jldoctest
julia> α = π;

julia> T = 500e-6;

julia> ω1 = α/T;

julia> B1 = 1;

julia> ω0 = 0;

julia> m0s = 0.1;

julia> R1f = 1;

julia> R2f = 15;

julia> Rx = 30;

julia> R1s = 6.5;

julia> R2s = 1e5;

julia> m0 = [0, 0, 1-m0s, 0, m0s, 1];

julia> (xf, yf, zf, xs, zs, _) = exp(hamiltonian_linear(ω1, B1, ω0, T, m0s, R1f, R2f, Rx, R1s, R2s)) * m0
6-element StaticArraysCore.SVector{6, Float64} with indices SOneTo(6):
  0.0010647535813058293
  0.0
 -0.8957848274535014
  0.005126529591877105
  0.08122007142111888
  1.0
```
