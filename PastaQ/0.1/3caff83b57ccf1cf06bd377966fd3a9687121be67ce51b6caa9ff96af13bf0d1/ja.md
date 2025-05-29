```
gatelayer(gatename::AbstractString, n::Int; kwargs...)
```

`gatename`で識別される`n`個の同一の量子ゲートを含む均一なレイヤーを作成します。追加のパラメータが提供される場合、それらはすべてのゲートに同様に追加されます。

```julia
gatelayer("H",3)
# 3-element Vector{Tuple{String, Int64}}:
#  ("H", 1)
#  ("H", 2)
#  ("H", 3)

gatelayer("X",1:2:5)
# 3-element Vector{Tuple{String, Int64}}:
#  ("X", 1)
#  ("X", 3)
#  ("X", 5)
```
