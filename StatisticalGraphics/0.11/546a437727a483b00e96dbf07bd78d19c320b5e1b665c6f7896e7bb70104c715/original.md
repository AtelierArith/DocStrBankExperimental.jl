```
sggrid(sgps...; opts...)
```

Position a collection of SG plots within a grid. The `opts...` refers to extra keyword arguments which can be passed to `sggrid`. 

# Keyword arguments

## Plot appearance

  * `align`: Determine how to align plots. It can be one of `:all`, `:each`, or `:none`. default: `:none`
  * `backcolor`: The back color.
  * `bordercolor`: The color for the border of plots. default: `:transparent`
  * `bounds`: One of `:full` or `:flush`. See `vega` docs for more information. default: `:full`
  * `center`: The row and column centering, respectively. default: `Bool[0, 0]`
  * `columns`: Number of columns to be created.
  * `columnspace`: Space between columns. default: `0`
  * `rowspace`: Space between rows. default: `0`
