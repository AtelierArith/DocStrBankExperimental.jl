```
dipole_temperature(dir; params::DipoleParameters = DipoleParameters())
dipole_temperature(dir, freq_hz; params::DipoleParameters = DipoleParameters())
```

Compute the temperature of the dipole along the direction `dir`, which should be a 3 - element array containing the XYZ components of the pointing vector.The vector must be expressed in the same coordinates as the vector used to specify the dipole in `params`, which is an object of type `DipoleParameters`.(Hint:if you created this object calling the constructor without arguments, as in `DipoleParameters()`, Ecliptic coordinates will be used.)

If `freq_hz` is specified, a relativistic frequency - dependent correction is applied.

# See also

If you need to compute the temperature caused by any other kinetic component (e.g., the orbital dipole caused by the motion of the spacecraft), use [`doppler_temperature`](@ref).

# Example

```julia
julia> dipole_temperature([0, 0, 1])
-0.0006532169921239991

julia> dipole_temperature([0, 0, 1], params=DipoleParameters(speed_m_s=371e3))
-0.0006548416782232279

julia> dipole_temperature([0, 0, 1], 30e9, params=DipoleParameters(speed_m_s=371e3))
-0.0006527515338213527
```
