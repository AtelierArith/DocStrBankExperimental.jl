```
`determine_E(inputs...)`
```

与えられた各入力を含むすべてのE系列を決定します。入力はカンマ区切りです。出力は可能な系列の名前のベクトルで、`Symbol`として返されます。

# 例

```julia-repl
julia> determine_E(220, 470, 680)
3-element Vector{Symbol}:
 :E6
 :E12
 :E24

julia> determine_E(220, 470, 910)
1-element Vector{Symbol}:
 :E24
```
