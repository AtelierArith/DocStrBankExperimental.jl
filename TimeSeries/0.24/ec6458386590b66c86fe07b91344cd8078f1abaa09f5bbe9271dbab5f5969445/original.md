```
rename(ta::TimeArray, colnames::Vector{Symbol})
rename(ta::TimeArray, colname::Symbol)
rename(ta::TimeArray, orig => new, ...)
rename(f::Base.Callable, ta, colnametyp)
```

Rename the columns of a `TimeArray`.

See also [`rename!`](@ref).

# Arguments

  * `colnametyp` is the input type for the function `f`. The valid value is `Symbol` or `String`.
