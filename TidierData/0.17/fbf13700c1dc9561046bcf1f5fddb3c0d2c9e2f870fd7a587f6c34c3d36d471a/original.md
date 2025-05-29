```
is_float(column::AbstractVector)
```

Determine if the given column contains floating-point numbers.

# Arguments

  * `column::AbstractVector`: The column whose data type needs to be checked.

# Returns

  * `Bool`: `true` if the column contains floating-point numbers, `false` otherwise.

# Examples

```jldoctest
julia> df = DataFrame(b = [missing, 2, 3],
                      c = [missing, 2.2, 34],
                      d = [missing, missing, "A"]);

julia> is_float(df.c)
true

julia> is_float(df.b)
false
```
