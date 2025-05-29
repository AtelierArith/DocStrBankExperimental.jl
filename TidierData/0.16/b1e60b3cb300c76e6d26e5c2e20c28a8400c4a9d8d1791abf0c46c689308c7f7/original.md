```
is_string(column::AbstractVector)
```

Determine if the given column contains strings.

# Arguments

  * `column::AbstractVector`: The column whose data type needs to be checked.

# Returns

  * `Bool`: `true` if the column contains strings, `false` otherwise.

# Examples

```jldoctest
julia> df = DataFrame(b = [missing, 2, 3],
                      c = [missing, 2.2, 34],
                      d = [missing, missing, "A"]);

julia> is_string(df.d)
true

julia> is_string(df.c)
false
```
