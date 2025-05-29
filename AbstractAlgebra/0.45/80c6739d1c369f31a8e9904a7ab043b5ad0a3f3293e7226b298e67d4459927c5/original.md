```
ordinal_number_string(number::Int)
```

A helper function which returns `number` as a string in ordinal form.

# Examples

```jldoctest; setup = :(using AbstractAlgebra; ordinal_number_string=AbstractAlgebra.ordinal_number_string)
julia> ordinal_number_string(1)
"1st"

julia> ordinal_number_string(2)
"2nd"

julia> ordinal_number_string(3)
"3rd"

julia> ordinal_number_string(4)
"4th"
```
