```julia
makeisolevels(func, levels, limits, colorbarticks)

```

Update levels, limits, colorbartics based on vector given in func.

  * if `limits[1]>limits[2]`, replace it by `extrema(func)`.
  * if levels is a number, replace it with a linear range in `limits` of length levels+2
  * if colorbarticks is `nothing` replace it with levels and add the limits to the result otherwise, if it is a number, replace it  with a linear range of corresponding length
