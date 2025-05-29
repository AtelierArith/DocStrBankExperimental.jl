```
p_ciic, v_ciic = ciic_pressure(model, T; p0 = nothing, v0 = nothing)
```

Calculate the Characteristic Isobaric Inflection Curve (CIIC) point at a given temperature for a thermodynamic model.

The CIIC represents points of maximum isobaric heat capacity (Cp) along isotherms, in contrast to Widom lines which represent maxima of Cp along isobars.

# Arguments

  * `model`: Thermodynamic model used for calculations
  * `T`: Temperature at which to calculate the CIIC pressure
  * `p0`: Optional initial pressure guess. If not provided, a default value will be used
  * `v0`: Optional initial volume guess. If not provided, a default value will be used

# Returns

  * `p_ciic`: Pressure at the CIIC point for the specified temperature
  * `v_ciic`: Volume at the CIIC point

# Example

```julia
model = PCSAFT(["methane"])
T = 200.0  # 200 K
p_ciic, v_ciic = ciic_pressure(model, T)
```
