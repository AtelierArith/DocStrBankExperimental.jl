```
check_filters(node; scale = nothing, symbol = nothing, link = nothing)
```

フィルターが適用されるmtgと一貫しているか確認します

# 例

```julia
check_filters(mtg, scale = 1)
check_filters(mtg, scale = (1,2))
check_filters(mtg, scale = (1,2), symbol = "Leaf", link = "<")
```
