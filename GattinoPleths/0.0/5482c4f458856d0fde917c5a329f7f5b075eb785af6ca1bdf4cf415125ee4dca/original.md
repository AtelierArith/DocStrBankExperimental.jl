```julia
scale!(con::Context, w::Int64, h::Int64, x::Int64 = 0, y::Int64 = 0)
```

Scales a `Gattino` `Context`to `w` and `h` dimensions from position `y`. This allows us to  zoom into our visualization, or set a certain part of our visualization to be visualized. –-

```example
pleth2 = choropleth(["de", "fr", "it"], [5, 45, 30], GattinoPleths.euromote_test, red_and_blue)
scale!(pleth2, 500, 500, 200, 250)
```
