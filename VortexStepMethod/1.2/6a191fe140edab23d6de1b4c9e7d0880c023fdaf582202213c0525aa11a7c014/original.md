```
BodyAerodynamics(wings::Vector{T}; 
                 kite_body_origin=zeros(MVec3)) where T <: AbstractWing
```

Construct a [BodyAerodynamics](@ref) object for aerodynamic calculations.

This constructor handles initialization of panels, coordinate transformations, and aerodynamic properties, returning a fully initialized structure ready for simulation.

# Arguments

  * `wings::Vector{T}`: Vector of wings to analyze, where T is an AbstractWing type

# Keyword Arguments

  * `kite_body_origin=zeros(MVec3)`: Origin point of kite body reference frame in CAD reference frame
  * `va=[15.0, 0.0, 0.0]`: Apparent wind vector
  * `omega=zeros(3)`: Turn rate in kite body frame x y and z

# Returns

  * [BodyAerodynamics](@ref) object initialized with panels and wings

# Example

```julia
wing = RamAirWing("body.obj", "foil.dat")
body_aero = BodyAerodynamics([wing], va=[15.0, 0.0, 0.0], omega=zeros(3))
```
