```
ParenthesesNotation <: RepeatingDecimalNotation
```

A type to represent a repeating decial with parentheses notation like "0.1(6)".

```jldoctest
julia> rd"123.45(678)"
4111111//33300

julia> no = ParenthesesNotation()
ParenthesesNotation()

julia> stringify(no, 1//11)
"0.(09)"

julia> rationalify(no, "123.45(678)")
4111111//33300
```
