```
@hydroflux(name, eqs...)
```

Create a `HydroFlux` from a set of equations, where:

  * Left sides of equations are output variables
  * Right sides contain input variables and parameters
  * Parameters are identified using ModelingToolkit's `isparameter`
  * `name` is an optional name for the flux (provide as first argument)

# Examples

```julia
@variables x, y, z
@parameters a, b

# Create a named flux with one equation
flux1 = @hydroflux :my_flux z = a*x + b*y

# Create a flux with multiple equations
flux2 = @hydroflux begin
    z₁ = a*x + b*y
    z₂ = x^2 + y^2
end
```
