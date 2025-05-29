```
EllipsisNotation <: RepeatingDecimalNotation
```

エリプシス表記を用いて繰り返し小数を表す型で、例えば「0.1666...」のようになります。

```jldoctest
julia> rd"123.45678678..."
4111111//33300

julia> no = EllipsisNotation()
EllipsisNotation()

julia> stringify(no, 1//11)
"0.0909..."

julia> rationalify(no, "123.45678678...")
4111111//33300

julia> rd"0.4545..."      # 0.(45)と同じ、[45]が2回繰り返される
5//11

julia> rd"0.333..."       # 0.(3)と同じ、1桁の[3]が3回繰り返される
1//3

julia> rd"0.13331333..."  # 0.(1333)と同じ、[1333]の繰り返しが[3]の繰り返しより優先される
1333//9999

julia> rd"0.133313333..." # 0.13331(3)と同じ、追加の[3]が曖昧さを解消する。
19997//150000
```
