```
DotsNotation <: RepeatingDecimalNotation
```

括弧表記の繰り返し小数を表す型、例えば「0.1(6)」のように。

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
