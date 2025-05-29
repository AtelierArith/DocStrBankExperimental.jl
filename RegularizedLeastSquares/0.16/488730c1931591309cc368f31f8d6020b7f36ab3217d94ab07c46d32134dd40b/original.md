```
norm(regType::Type{<:AbstractParameterizedRegularization}, x, λ; kwargs...)
```

construct a regularization term of type `regType` with given `λ` and `kwargs` and apply its `norm` on `x`
