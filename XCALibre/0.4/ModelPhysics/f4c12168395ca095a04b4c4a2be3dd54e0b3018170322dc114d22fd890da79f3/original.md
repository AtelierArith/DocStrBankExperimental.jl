```
Ttoh!(model::Physics{T1,F,M,Tu,E,D,BI}, T::ScalarField, h::ScalarField
) where {T1,F<:AbstractCompressible,M,Tu,E,D,BI}
```

Function coverts temperature ScalarField to sensible enthalpy ScalarField.

### Input

  * `model`  – Physics model defined by user.
  * `T`      – Temperature ScalarField.
  * `h`      – Sensible enthalpy ScalarField.
