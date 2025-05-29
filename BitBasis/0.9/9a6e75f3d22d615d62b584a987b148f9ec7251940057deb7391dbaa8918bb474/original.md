```
bmask(::Type{T}) where T <: Integer -> zero(T)
bmask([T::Type], positions::Int...) -> T
bmask([T::Type], range::UnitRange{Int}) -> T
```

Return an integer mask of type `T` where `1` is the position masked according to `positions` or `range`. Directly use `T` will return an empty mask `0`.
