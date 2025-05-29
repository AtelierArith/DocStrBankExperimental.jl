```
ordinal(num) -> result
```

### Purpose

Convert an integer to a correct English ordinal string.

### Explanation

The first four ordinal strings are "1st", "2nd", "3rd", "4th", ....

### Arguments

  * `num`: number to be made ordinal. It should be of type `Integer`.

### Output

  * `result`: ordinal string, such as "1st", "3rd", "164th", "87th", etc.

### Example

```jldoctest
julia> using AstroLib

julia> ordinal.(1:5)
5-element Vector{String}:
 "1st"
 "2nd"
 "3rd"
 "4th"
 "5th"
```

### Notes

This function does not support float arguments, unlike the IDL implementation. Code of this function is based on IDL Astronomy User's Library.
