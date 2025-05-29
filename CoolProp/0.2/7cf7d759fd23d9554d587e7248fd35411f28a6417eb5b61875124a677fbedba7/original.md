```
set_reference_state(ref::AbstractString, reference_state::AbstractString)
```

Set the reference state based on a string representation.

#Arguments

  * `fluid::AbstractString`	The name of the fluid (Backend can be provided like "REFPROP::Water", or if no backend is provided, "HEOS" is the assumed backend)
  * `reference_state::AbstractString`	The reference state to use, one of:

| Reference State | Description                                        |
|:--------------- |:-------------------------------------------------- |
| "IIR"           | h = 200 kJ/kg, s=1 kJ/kg/K at 0C saturated liquid  |
| "ASHRAE"        | h = 0, s = 0 @ -40C saturated liquid               |
| "NBP"           | h = 0, s = 0 @ 1.0 bar saturated liquid            |
| "DEF"           | Reset to the default reference state for the fluid |
| "RESET"         | Remove the offset                                  |

#Example

```julia
julia> h0=-15870000.0; # J/kg
julia> s0= 3887.0; #J/kg
julia> rho0=997.1;
julia> T0=298.15;
julia> M = PropsSI("molemass", "Water");
julia> set_reference_stateD("Water", T0, rho0/M, h0*M, s0*M);
julia> PropsSI("H", "T", T0, "P", 101325, "Water")
-1.5870107493843542e7
julia> set_reference_stateS("Water", "DEF");
julia> PropsSI("H", "T", T0, "P", 101325, "Water")
104920.1198093371
```

#Ref set*reference*stateS(const std::string& FluidName, const std::string& reference_state)

#Note The changing of the reference state should be part of the initialization of your program, and it is not recommended to change the reference state during the course of making calculations
