```
SensibleEnthalpy <: AbstractEnergyModel
```

Type that represents energy model, coefficients and respective fields.

### Fields

  * 'h'    – Sensible enthalpy ScalarField.
  * 'T'    – Temperature ScalarField.
  * 'hf'   – Sensible enthalpy FaceScalarField.
  * 'Tf'   – Temperature FaceScalarField.
  * 'K'    – Specific kinetic energy ScalarField.
  * 'dpdt' – Pressure time derivative ScalarField.
  * 'updated_BC' – Boundary condition function to convert temperature to sensible enthalp on                    on a fixed value boudary.
  * 'coeffs' – A tuple of model coefficients.
