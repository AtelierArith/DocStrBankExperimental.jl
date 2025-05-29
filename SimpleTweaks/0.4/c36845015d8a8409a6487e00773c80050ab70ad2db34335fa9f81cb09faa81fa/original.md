```
find_first_occurrence(array::AbstractArray{T}, val::T) where {T} -> Union(nothing,Int)
```

Searches the `array` for the `val` and returns the index of the first occurrence.

# Arguments

  * `array::AbstractArray{T}`: the array to search,
  * `val::T`: the value to search for,

# Keywords

# Returns

  * `Int`: the index where `val` is located in the `array`, or `nothing` if `val` is not found in `array`.

# Throws
