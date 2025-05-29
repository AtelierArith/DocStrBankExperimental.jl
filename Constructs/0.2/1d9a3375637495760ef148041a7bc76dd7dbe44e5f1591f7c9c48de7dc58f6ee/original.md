```
validate(validator::Validator{T}, obj::T; contextkw...) -> Bool
```

Checks whether the given `obj` is a valid value for the `validator`.

Should return a `Bool` or throw a [`ValidationError`](@ref).
