```
function pack_xy(data; kw...)
```

Return Tuple (x,y) substracted from points or positions of particles in data. Useful to prepare a plot.

# Keywords

  * `xaxis`: `Symbol` to extract on x-axis. Default is `:x`
  * `yaxis`: `Symbol` to extract on y-axis. Defualt is `:y`
