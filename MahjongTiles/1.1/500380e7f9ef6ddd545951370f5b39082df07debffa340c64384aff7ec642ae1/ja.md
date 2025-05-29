```
wind(index)
wind(direction)
```

風のタイルを作成します。整数が使用される場合、標準的な中国の方位の順序が使用されます（すなわち、`1` -> 東、`2` -> 南、`3` -> 西、`4` -> 北）。それ以外の場合、方向の名前には記号も使用できます（例：`:east`, `:north`）。

## 例

```jldoctest
julia> wind(:north)
🀃

julia> wind(2)
🀁
```
