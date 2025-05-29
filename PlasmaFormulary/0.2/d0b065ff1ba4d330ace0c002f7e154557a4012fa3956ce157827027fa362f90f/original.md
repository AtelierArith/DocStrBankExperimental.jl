```
ion_sound_speed(T_e, T_i, m_i, Z; γ_e=1, γ_i=3, n_e=nothing, k=nothing)
```

Calculate the ion sound speed for an electron-ion plasma given by:

$$
V_S = \sqrt{\frac{γ_e Z k_B T_e + γ_i k_B T_i}{m_i (1 + k^2 λ_{D}^2)}}
$$

If both `n_e` and `k` are given, includes dispersive correction.

# Arguments

  * `T_e`: Electron temperature (`K` or energy per particle)
  * `T_i`: Ion temperature (`K` or energy per particle)
  * `m_i`: Ion mass
  * `Z`: Ion charge state (default: 1)
  * `γ_e`: Electron adiabatic index (default: 1)
  * `γ_i`: Ion adiabatic index (default: 3)
  * `n_e`: Electron number density (optional)
  * `k`: Wavenumber (optional)
