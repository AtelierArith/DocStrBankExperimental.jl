```
check_filters(node; scale = nothing, symbol = nothing, link = nothing)
```

Check if the filters are consistant with the mtg onto which they are applied

# Examples

```julia
check_filters(mtg, scale = 1)
check_filters(mtg, scale = (1,2))
check_filters(mtg, scale = (1,2), symbol = "Leaf", link = "<")
```
