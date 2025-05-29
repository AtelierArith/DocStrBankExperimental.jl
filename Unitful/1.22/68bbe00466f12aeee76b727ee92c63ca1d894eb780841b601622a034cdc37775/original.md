```
show(io::IO, x::Quantity)
```

Show a unitful quantity by calling [`showval`](@ref) on the numeric value, appending a space, and then calling `show` on a units object `U()`.
