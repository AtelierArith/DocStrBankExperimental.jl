```
ordinal_number_string(number::Int)
```

数値を序数形式の文字列として返すヘルパー関数です。

# 例

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
