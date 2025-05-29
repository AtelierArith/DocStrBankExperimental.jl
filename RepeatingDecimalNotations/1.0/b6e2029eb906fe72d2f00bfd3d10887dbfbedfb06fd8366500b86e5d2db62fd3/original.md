```
DotsNotation <: RepeatingDecimalNotation
```

A type to represent a repeating decial with parentheses notation like "0.1(6)".

```jldoctest
julia> rd"123.456̇78̇"
4111111//33300

julia> no = DotsNotation()
DotsNotation()

julia> stringify(no, 1//11)
"0.0̇9̇"

julia> rationalify(no, "123.456̇78̇")
4111111//33300
```
