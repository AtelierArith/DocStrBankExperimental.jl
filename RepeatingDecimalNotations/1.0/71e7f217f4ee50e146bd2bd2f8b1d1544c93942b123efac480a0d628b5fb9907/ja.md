```
ParenthesesNotation <: RepeatingDecimalNotation
```

括弧表記を用いて繰り返し小数を表す型で、例えば「0.1(6)」のようになります。

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
