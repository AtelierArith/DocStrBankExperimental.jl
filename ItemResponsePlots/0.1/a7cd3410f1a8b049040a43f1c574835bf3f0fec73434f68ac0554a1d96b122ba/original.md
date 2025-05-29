```
itemplot(model, item, args...; kwargs...)
```

Create an item plot for `item` of `model`.

The resulting item plot contains the item characteristic curve (left) and the item information curve (right).

The additional `args...` and `kwargs...` are passed to the lower level functions [`item_characteristic_curve`](@ref) and [`item_information_curve`](@ref).
