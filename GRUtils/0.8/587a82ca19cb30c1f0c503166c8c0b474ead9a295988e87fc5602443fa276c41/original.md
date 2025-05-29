```
xflip(flag)
yflip(flag)
zflip(flag)
```

Reverse the direction of the X-, Y- or Z-axis (`flag == true`), or set them back to their normal direction (`flag == false` ).

Use the keyword argument `xflip=<true/false>`, etc. in plotting functions, to set reversed axes during the creation of plots.

# Examples

```julia
# Reverse the x-axis
xflip(true)
# Ensure that the y-axis is not reversed
yflip(false)
```
