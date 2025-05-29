```
objective!(model::AbstractSem, params)
```

Returns the objective value at `params`. The model object can be modified.

# Implementation

To implement a new `SemImplied` or `SemLossFunction` subtype, you need to add a method for     objective!(newtype::MyNewType, params, model::AbstractSemSingle)

To implement a new `AbstractSem` subtype, you need to add a method for     objective!(model::MyNewType, params)
