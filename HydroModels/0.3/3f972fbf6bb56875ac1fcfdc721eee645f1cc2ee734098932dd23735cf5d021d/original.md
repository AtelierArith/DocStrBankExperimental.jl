```
stateflux(name, eq)
```

Create a `StateFlux` from an equation, where:

  * Left side of the equation is the state variable
  * Right side contains the expression for the state variable's change
  * `name` is an optional name for the flux (provide as first argument)

# Examples

```julia
@variables x, y, z
@parameters a, b

# Create a named state flux
flux1 = @stateflux_build :my_flux z = a*x + b*y

# Create a state flux without a name
flux2 = @stateflux_build z = a*x + b*y
```
