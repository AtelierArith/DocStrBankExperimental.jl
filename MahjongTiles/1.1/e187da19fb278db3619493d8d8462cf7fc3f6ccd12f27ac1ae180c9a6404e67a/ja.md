```
dragon(index)
dragon(name)
```

風タイルを作成します。整数が使用される場合、標準の順序が使用されます（すなわち、`1` -> 赤ドラゴン、`2` -> 緑ドラゴン、`3` -> 白ドラゴン）。それ以外の場合、名前/色のためにシンボルも使用できます（例：`:red`、`:green`）。

## 例

```jldoctest
julia> dragon(:red)
🀄

julia> dragon(2)
🀅
```
