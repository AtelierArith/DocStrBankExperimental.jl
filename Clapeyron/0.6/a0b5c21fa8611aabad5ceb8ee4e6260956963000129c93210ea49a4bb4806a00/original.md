```
Tw, vw = widom_temperature(model, p; T0 = nothing, v0 = nothing)
```

Calculate the Widom temperature and corresponding volume at a given pressure for a thermodynamic model.

The Widom point represents the temperature where maxima of the isobaric heat capacity occurs along an isobar in the supercritical region. In particular, `widom_temperature` calculates the widom point at a specified temperature.

# Arguments

  * `model`: Thermodynamic model used for calculations
  * `p`: Pressure at which to calculate the Widom temperature
  * `T0`: Optional initial temperature guess. If not provided, a default value will be used
  * `v0`: Optional initial volume guess. If not provided, a default value will be used

# Returns

  * `Tw`: Widom temperature at the specified pressure
  * `vw`: Volume at the Widom temperature and specified pressure

# Example

```julia
model = PCSAFT(["methane"])
p = 150e5  #150 bar, over critical pressure
Tw, vw = widom_temperature(model, p)
```
