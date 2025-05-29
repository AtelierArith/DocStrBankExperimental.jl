```
Try{T} = Union{Const{<:Exception}, Identity{T}}
@Try(error("something happend")) isa Const(<:Thrown{ErrorException})
@Try(:successfull) == Identity(:successfull)
```

A specific case of [`Either`](@ref), where the Failure is always an Exception. This can be used as an alternative to using try-catch syntax and allows for very flexible error handling, as the error is now captured in a proper defined type. Often it is really handy to treat errors like other values (without the need of extra try-catch syntax which only applies to exceptions).

We reuse [`Identity`](@ref) for representing the single-element-container and `Const(<:Exception)` as the Exception thrown.
