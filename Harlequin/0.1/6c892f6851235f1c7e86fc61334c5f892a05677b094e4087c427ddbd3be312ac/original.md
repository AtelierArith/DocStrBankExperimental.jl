This structure encodes the information needed to estimate the contribution of the temperature of the CMB dipole caused by the motion of the Solar System with respect to the CMB rest frame.

# Fields

  * `solsysdir_theta_rad`: colatitude (in radians) of the dipole axis
  * `solsysdir_phi_rad`: longitude (in radians) of the dipole axis
  * `solsys_speed_m_s`: speed (in m/s) of the reference frame with respect to the CMB
  * `solsys_velocity_m_s`: velocity 3-vector (in m/s) of the reference frame with respect to the CMB
  * `tcmb_k`: thermodynamic temperature (in Kelvin) of the CMB

# Object creation

The simplest way to create a `DipoleParameters` object is to call the constructor without arguments. In this case, the dipole axis will be provided in Ecliptic coordinates, using the estimate by Planck 2015, and the best COBE estimate for the CMB monopole temperature will be used. Otherwise, you can pass any of the following keywords to set the parameters:

  * `theta_rad` defaults to `SOLSYSDIR_ECL_THETA`
  * `phi_rad` defaults to `SOLSYSDIR_ECL_PHI`
  * `speed_m_s` defaults to `SOLSYSSPEED_M_S`
  * `t_k` defaults to `T_CMB`

Here is an example where we produce a dipole that is 10% stronger than Planck's:

```julia
using Harlequin # hide
dip = DipoleParameters(speed_m_s = SOLSYS_SPEED_VEC_M_S * 1.10)
```
