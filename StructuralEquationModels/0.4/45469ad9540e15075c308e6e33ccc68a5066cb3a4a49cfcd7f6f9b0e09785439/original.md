```
hessian!(hessian, model::AbstractSem, params)
```

Writes the hessian value at `params` to `hessian`.

# Implementation

To implement a new `SemImplied` or `SemLossFunction` type, you can add a method for     hessian!(newtype::MyNewType, params, model::AbstractSemSingle)

To implement a new `AbstractSem` subtype, you can add a method for     hessian!(hessian, model::MyNewType, params)
