```
is_integer(column::AbstractVector)
```

Determine if the given column contains integers.

# Arguments

  * `column::AbstractVector`: The column whose data type needs to be checked.

# Returns

  * `Bool`: `true` if the column contains integers, `false` otherwise.

# Examples

```jldoctest
julia> df = DataFrame(b = [missing, 2, 3],
                      c = [missing, 2.2, 34],
                      d = [missing, missing, "A"]);

julia> is_integer(df.b)
true

julia> is_integer(df.d)
false
```
