```julia
scale!(con::Context, w::Int64, h::Int64, x::Int64 = 0, y::Int64 = 0)
```

`Gattino` `Context`を位置`y`から`w`と`h`の寸法にスケーリングします。これにより、視覚化をズームインしたり、視覚化の特定の部分を表示することができます。 –-

```example
pleth2 = choropleth(["de", "fr", "it"], [5, 45, 30], GattinoPleths.euromote_test, red_and_blue)
scale!(pleth2, 500, 500, 200, 250)
```
