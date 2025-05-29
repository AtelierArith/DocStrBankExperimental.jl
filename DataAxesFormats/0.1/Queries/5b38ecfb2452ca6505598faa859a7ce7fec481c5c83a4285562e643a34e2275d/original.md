```
IsMatch(value::Union{AbstractString, Regex}) <: QueryOperation
```

Similar to [`IsLess`](@ref) except that the compared values must be strings, and the mask is of the values that match the given regular expression.
