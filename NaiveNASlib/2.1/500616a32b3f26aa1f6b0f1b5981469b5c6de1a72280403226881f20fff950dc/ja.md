```
inputvertex(name, size)
```

指定された `name` と `size` を持つ不変の入力タイプの頂点を返します。

通常、計算グラフへの「エントリ」ポイントとして使用されます。

# 例

```jldoctest
julia> using NaiveNASlib

julia> inputvertex("input", 5)
InputSizeVertex(InputVertex(input, outputs=[]), 5)

```
