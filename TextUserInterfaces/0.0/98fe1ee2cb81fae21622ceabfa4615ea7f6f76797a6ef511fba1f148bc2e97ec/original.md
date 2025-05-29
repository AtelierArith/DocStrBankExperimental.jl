```
function init_color(name::Symbol, r::Int, g::Int, b::Int)
```

Initialize the color with name `name` and RGB color `r`, `g`, and `b`.  Notice that the range for the last three variables is `[0,1000]`.

If the color is already initialized, then nothing will be changed.

If the color was initialized, then it returns the color ID. Otherwise, it returns `-1`.
