```
ScientificNotation <: RepeatingDecimalNotation
```

科学的表記法を用いて繰り返し小数を表す型、例えば「0.1r6」のようなものです。

```jldoctest
julia> rd"123.45r678"
4111111//33300

julia> no = ScientificNotation()
ScientificNotation()

julia> stringify(no, 1//11)
"0.r09"

julia> rationalify(no, "123.45r678")
4111111//33300

julia> rd"1.2345r678e2"  # 指数項がサポートされています。
4111111//33300
```
