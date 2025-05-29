```
simshow(arr; set_zero=false, set_one=false, γ=1, cmap=:gray)
```

Displays a real valued array. Works within Jupyter and Pluto.

# Keyword args

The transforms are applied in that order.

  * `set_zero=false` subtracts the minimum to set minimum to 0
  * `set_one=true` divides by the maximum to set maximum to 1
  * `γ` applies a gamma correction
  * `cmap=:gray` applies a colormap provided by ColorSchemes.jl. If `cmap=:gray` simply `Colors.Gray` is used   and with different colormaps the result is an `Colors.RGB` element type.     You can try `:jet`, `:deep`, `thermal` or different ones by reading the catalogue of ColorSchemes.jl
