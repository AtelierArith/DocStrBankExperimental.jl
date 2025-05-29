```
get_input_pair_index(pair::AbstractString)
```

Get the index for an input pair "PT*INPUTS", "HmolarQ*INPUTS", etc, for `abstractstate_update()` function.

# Arguments

  * `pair::AbstractString`: The name of an input pair, described in the following table

| Input Pair          | Description                                        |
|:------------------- |:-------------------------------------------------- |
| QT_INPUTS           | Molar quality, Temperature in K                    |
| QSmolar_INPUTS      | Molar quality, Entropy in J/mol/K                  |
| QSmass_INPUTS       | Molar quality, Entropy in J/kg/K                   |
| HmolarQ_INPUTS      | Enthalpy in J/mol, Molar quality                   |
| HmassQ_INPUTS       | Enthalpy in J/kg, Molar quality                    |
| DmassQ_INPUTS       | Molar density kg/m^3, Molar quality                |
| DmolarQ_INPUTS      | Molar density in mol/m^3, Molar quality            |
| PQ_INPUTS           | Pressure in Pa, Molar quality                      |
| PT_INPUTS           | Pressure in Pa, Temperature in K                   |
| DmassT_INPUTS       | Mass density in kg/m^3, Temperature in K           |
| DmolarT_INPUTS      | Molar density in mol/m^3, Temperature in K         |
| HmassT_INPUTS       | Enthalpy in J/kg, Temperature in K                 |
| HmolarT_INPUTS      | Enthalpy in J/mol, Temperature in K                |
| SmassT_INPUTS       | Entropy in J/kg/K, Temperature in K                |
| SmolarT_INPUTS      | Entropy in J/mol/K, Temperature in K               |
| TUmass_INPUTS       | Temperature in K, Internal energy in J/kg          |
| TUmolar_INPUTS      | Temperature in K, Internal energy in J/mol         |
| DmassP_INPUTS       | Mass density in kg/m^3, Pressure in Pa             |
| DmolarP_INPUTS      | Molar density in mol/m^3, Pressure in Pa           |
| HmassP_INPUTS       | Enthalpy in J/kg, Pressure in Pa                   |
| HmolarP_INPUTS      | Enthalpy in J/mol, Pressure in Pa                  |
| PSmass_INPUTS       | Pressure in Pa, Entropy in J/kg/K                  |
| PSmolar_INPUTS      | Pressure in Pa, Entropy in J/mol/K                 |
| PUmass_INPUTS       | Pressure in Pa, Internal energy in J/kg            |
| PUmolar_INPUTS      | Pressure in Pa, Internal energy in J/mol           |
| DmassHmass_INPUTS   | Mass density in kg/m^3, Enthalpy in J/kg           |
| DmolarHmolar_INPUTS | Molar density in mol/m^3, Enthalpy in J/mol        |
| DmassSmass_INPUTS   | Mass density in kg/m^3, Entropy in J/kg/K          |
| DmolarSmolar_INPUTS | Molar density in mol/m^3, Entropy in J/mol/K       |
| DmassUmass_INPUTS   | Mass density in kg/m^3, Internal energy in J/kg    |
| DmolarUmolar_INPUTS | Molar density in mol/m^3, Internal energy in J/mol |
| HmassSmass_INPUTS   | Enthalpy in J/kg, Entropy in J/kg/K                |
| HmolarSmolar_INPUTS | Enthalpy in J/mol, Entropy in J/mol/K              |
| SmassUmass_INPUTS   | Entropy in J/kg/K, Internal energy in J/kg         |
| SmolarUmolar_INPUTS | Entropy in J/mol/K, Internal energy in J/mol       |

# Example

```julia
julia> get_input_pair_index("PT_INPUTS")
9
```
