```
HrseReadOptions(kwargs...)
```

Stores options for parsing HRSE files.

# Arguments

  * `integertypes = [Int64, BigInt]`: A list of signed integer types to try parsing integers as. The first type that can   represent the integer will be used.
  * `floattype = Float64`: The floating point type to parse floating point numbers as.
  * `readcomments = false`: Whether to read comments and store them in `CommentedElement` objects; if false, comments are  ignored.
  * `extensions`: A collection of [`Extension`](@ref)s to HRSE.

See also [`readhrse`](@ref).
