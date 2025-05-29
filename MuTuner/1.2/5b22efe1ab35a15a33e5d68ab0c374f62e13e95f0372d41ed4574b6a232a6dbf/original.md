```
MuTunerLogger{T<:AbstractFloat, S<:Number}
```

Type to assist with dynamically tuning the chemical potential $mu$ to achieve a target particle density $\langle n \rangle = n_0$.

# Fields

  * `n₀::T`: Target filling as intensive value $\langle n \rangle = n_0$.
  * `N₀::T`: Target filling as exensive quantity $\langle N \rangle = N_0 = V \cdot n_0$.
  * `β::T`: Inverse temperature.
  * `V::Int`: System size.
  * `u₀::T`: Intensive energy scale.
  * `α::T`: Extensive energy scale $\alpha = N / U_0$.
  * `c::T`: Fraction of history to discard when calculating averages.
  * `μ_tp1::T`: Next chemical potential value for time `t+1`.
  * `μ_bar::T`: Forgetful mean of the chemical potential.
  * `μ_var::T`: Forgetful variance of the chemical potential.
  * `N_bar::S`: Forgetful mean of the total particle number, accounting for the sign.
  * `N_var::T`: Forgetful variance of the total particle number, accounting for the sign.
  * `s_bar::T`: Forgetful mean of the sign.
  * `s_var::T`: Forgetful variance of the sign.
  * `N²_bar::S`: Forgetful mean of the square of total particle number, accounting for the sign.
  * `κ_bar::T`: Forgetful mean of the compressibility.
  * `μ_traj::Vector{T}`: Timeseries of chemical potential values, $\mu_t.$
  * `N_traj::Vector{S}`: Timeseries of total particle number values accounting for the sign, $s_t \cdot N_t.$
  * `s_traj::Vector{S}`: Timeseries of the sign, $s_t.$
  * `N²_traj::Vector{S}`: Timeseries of total particle number square values accounting for the sign, $s_t \cdot N^2_t.$
