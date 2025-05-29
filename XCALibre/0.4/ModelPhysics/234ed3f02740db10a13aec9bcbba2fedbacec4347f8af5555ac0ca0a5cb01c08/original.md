```
htoT!(model::Physics{T1,F,M,Tu,E,D,BI}, h::ScalarField, T::ScalarField
) where {T1,F<:AbstractCompressible,M,Tu,E,D,BI}
```

Function coverts sensible enthalpy ScalarField to temperature ScalarField.

### Input

  * `model`  – Physics model defined by user.
  * `h`      – Sensible enthalpy ScalarField.
  * `T`      – Temperature ScalarField.
