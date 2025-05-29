```
EllipsisNotation <: RepeatingDecimalNotation
```

A type to represent a repeating decial with ellipsis notation like "0.1666...".

```jldoctest
julia> rd"123.45678678..."
4111111//33300

julia> no = EllipsisNotation()
EllipsisNotation()

julia> stringify(no, 1//11)
"0.0909..."

julia> rationalify(no, "123.45678678...")
4111111//33300

julia> rd"0.4545..."      # Same as 0.(45), repeating [45] two times
5//11

julia> rd"0.333..."       # Same as 0.(3), repeating one digit [3] three times
1//3

julia> rd"0.13331333..."  # Same as 0.(1333), repeating [1333] has priority over repeating [3]
1333//9999

julia> rd"0.133313333..." # Same as 0.13331(3), adding additional [3] resolves the ambiguity.
19997//150000
```
