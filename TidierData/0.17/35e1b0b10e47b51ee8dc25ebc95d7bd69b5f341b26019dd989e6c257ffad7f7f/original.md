```
is_number(column::AbstractVector)
```

Determine if the given column contains numbers.

# Arguments

  * `column::AbstractVector`: The column whose data type needs to be checked.

# Returns

  * `Bool`: `true` if the column contains numbers, `false` otherwise.

# Examples

```jldoctest
julia> df = DataFrame(b = [missing, 2, 3],
                      c = [missing, 2.2, 34],
                      d = [missing, missing, "A"]);

julia> is_number(df.b)
true

julia> is_number(df.c)
true

julia> is_number(df.d)
false
```
