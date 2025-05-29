```
pw, vw = widom_pressure(model, T; p0 = nothing, v0 = nothing)
```

Calculate the Widom pressure and corresponding volume at a given temperature for a thermodynamic model.

The Widom point represents the temperature where maxima of the isobaric heat capacity occurs along an isobar in the supercritical region. In particular, `widom_pressure` calculates the widom point at a specified temperature.

# Arguments

  * `model`: Thermodynamic model used for calculations
  * `T`: Temperature at which to calculate the Widom pressure
  * `p0`: Optional initial pressure guess. If not provided, a default value will be used
  * `v0`: Optional initial volume guess. If not provided, a default value will be used

# Returns

  * `pw`: Widom pressure at the specified temperature
  * `vw`: Volume at the Widom pressure and specified temperature

# Example

```julia
model = PCSAFT(["methane"])
T = 200.0  # 200 K
pw, vw = widom_pressure(model, T)
```
