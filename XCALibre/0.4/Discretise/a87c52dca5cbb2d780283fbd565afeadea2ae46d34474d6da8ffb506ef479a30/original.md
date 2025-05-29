```
FixedTemperature <: AbstractDirichlet
```

Fixed temperature boundary condition model, which allows the user to specify wall temperature that can be translated to the energy specific model, such as sensivle enthalpy.

### Fields

  * 'ID' – Boundary ID
  * `value` – Scalar or Vector value for Dirichlet boundary condition.
  * `T` - Temperature value in Kelvin.
  * `model` - Energy physics model for case.

### Examples

```
FixedTemperature(:inlet, T=300.0, model=model.energy),
```
