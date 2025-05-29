```
set_reference_state(fluid::AbstractString, T::Real, rhomolar::Real, hmolar0::Real, smolar0::Real)
```

Set the reference state based on a thermodynamic state point specified by temperature and molar density.

#Arguments

  * `fluid::AbstractString`	The name of the fluid
  * `T::Real`	Temperature at reference state [K]
  * `rhomolar::Real`	Molar density at reference state [mol/m^3]
  * `hmolar0::Real`	Molar enthalpy at reference state [J/mol]
  * `smolar0::Real`	Molar entropy at reference state [J/mol/K]

#Ref set*reference*stateD(const char* Ref, double T, double rhomolar, double hmolar0, double smolar0)
