```
CategoricalValue{T <: Union{AbstractChar, AbstractString, Number}, R <: Integer}
```

A wrapper around a value of type `T` corresponding to a level in a `CategoricalPool`.

`CategoricalValue` objects are considered as equal to the value of type `T` they wrap by `==` and `isequal`. However, order comparisons like `<` and `isless` are only possible if [`isordered`](@ref) is `true` for the value's pool, and in that case the order of the pool's [`levels`](@ref DataAPI.levels) is used rather than the standard ordering of values of type `T`.
