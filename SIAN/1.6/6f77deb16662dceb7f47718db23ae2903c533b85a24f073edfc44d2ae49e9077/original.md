```
func get_parameters(ode; initial_conditions=true)
```

Retrieve parameters from the `ode` system. Retrieve initial conditions if `initial_conditions` is set `true`.

## Input

```
- `ode::ODE` - an ODE system
- `initial_conditions::Bool` - whether to extract initial conditions. Default `true`.
```

## Output

```
    - Array of parameters (and initial conditions).
```
