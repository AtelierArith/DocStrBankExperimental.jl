```
ReferenceState(type::Symbol = :no_set;T0 = NaN;P0 = NaN,H0 = NaN,S0 = NaN,phase = :unknown,z0 = Float64[])
```

Parameter used to define a reference state for enthalpy and entropy, normally stored in the ideal model.  when set, it calculates a set of `a0` and `a1` values such as the entropy and enthalpy at a specified point are fixed.

the `type` argument accepts the following standalone options:

  * `:no_set`: it returns the current defaults stablished by the equation of state.
  * `:ashrae`: h = s = 0 at -40°C saturated liquid
  * `:iir`: h = 200.0 kJ/kg, s=1.0 kJ/kg/K at 0C saturated liquid
  * `:nbp`: h = s = 0 at 1 atm saturated liquid
  * `:stp`: h = s = 0 at 1 bar, 0°C fluid of the most stable phase
  * `:stp_old`: h = s = 0 at 1 atm, 0°C fluid of the most stable phase
  * `:ntp`: h = s = 0 at 1 atm, 20°C fluid of the most stable phase

it also accepts the following options, that require additional specifications:

  * `:volume` h = H0, s = S0, at T = T0, v = `volume(model,P0,T0,z0,phase = phase)`
  * `:saturation_pressure` h = H0, s = S0, at T = T0, saturated phase (specified by the `phase` argument)
  * `:saturation_temperature` h = H0, s = S0, at p = P0, saturated phase (specified by the `phase` argument)

If `z0` is not specified, the reference state calculation will be done for each component separately.

## Examples

```
julia> model = PCSAFT(["water","pentane"],idealmodel = ReidIdeal,reference_state = ReferenceState(:nbp))
PCSAFT{ReidIdeal, Float64} with 2 components:
 "water"
 "pentane"
Contains parameters: Mw, segment, sigma, epsilon, epsilon_assoc, bondvol

julia> model2 = PCSAFT(["water","pentane"],idealmodel = ReidIdeal,reference_state = :nbp) #equivalent
PCSAFT{ReidIdeal, Float64} with 2 components:
 "water"
 "pentane"
Contains parameters: Mw, segment, sigma, epsilon, epsilon_assoc, bondvol

julia> pure = split_model(model)
2-element Vector{PCSAFT{ReidIdeal, Float64}}:
 PCSAFT{ReidIdeal, Float64}("water")
 PCSAFT{ReidIdeal, Float64}("pentane")

julia> T,vl,_ = saturation_temperature(pure[1],101325.0) #saturated liquid at 1 atm
(373.2706553019503, 2.0512186595412677e-5, 0.03006573003253086)

julia> enthalpy(pure[1],101325.0,T)
-5.477897970382323e-6

julia> entropy(pure[1],101325.0,T)
5.009221069190994e-9
```
