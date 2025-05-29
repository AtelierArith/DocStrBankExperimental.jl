```
prox!(regType::Type{<:AbstractProjectionRegularization}, x; kwargs...)
```

construct a regularization term of type `regType` with given `kwargs` and apply its `prox!` on `x`
