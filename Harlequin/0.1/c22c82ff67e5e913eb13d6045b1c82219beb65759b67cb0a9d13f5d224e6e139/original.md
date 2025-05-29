```
doppler_temperature(velocity_m_s, dir, tcmb_k)
doppler_temperature(velocity_m_s, dir, tcmb_k, freq_hz)
```

Compute the temperature caused by the motion by `velocity_m_s` (a 3-vector, in m/s) through the Doppler effect. If `freq_hz` is specified, the computation includes quadrupolar relativistic corrections.

# See also

If you need to compute the solar dipole caused by the motion of the Solar System with respect to the CMB rest frame, it is easier to use [`dipole_temperature`](@ref).

# Example
