```
T_ciic, v_ciic = ciic_temperature(model, p; T0 = nothing, v0 = nothing)
```

Calculate the Characteristic Isobaric Inflection Curve (CIIC) point at a given pressure for a thermodynamic model.

The CIIC represents points of maximum isobaric heat capacity (Cp) along isotherms, in contrast to Widom lines which represent maxima of Cp along isobars.

# Arguments

  * `model`: Thermodynamic model used for calculations
  * `p`: Pressure at which to calculate the CIIC temperature
  * `T0`: Optional initial temperature guess. If not provided, a default value will be used
  * `v0`: Optional initial volume guess. If not provided, a default value will be used

# Returns

  * `T_ciic`: Temperature at the CIIC point for the specified pressure
  * `v_ciic`: Volume at the CIIC point

# Example

```julia
model = PCSAFT(["methane"])
p = 150e5  # 150 bar
T_ciic, v_ciic = ciic_temperature(model, p)
```
