```
gradient!(gradient, model::AbstractSem, params)
```

Writes the gradient value at `params` to `gradient`.

# Implementation

To implement a new `SemImplied` or `SemLossFunction` type, you can add a method for     gradient!(newtype::MyNewType, params, model::AbstractSemSingle)

To implement a new `AbstractSem` subtype, you can add a method for     gradient!(gradient, model::MyNewType, params)
