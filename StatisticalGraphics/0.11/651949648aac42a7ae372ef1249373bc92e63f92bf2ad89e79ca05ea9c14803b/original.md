```
gradient([colors...]; direction = [0,1,0,0])
```

A linear gradient interpolates colors along a line, from a starting point to an ending point. By default a linear gradient runs horizontally, from left to right. Use the direction to configure the gradient direction, e.g. [0,0,0,1] runs the gradient vertically. All coordinates are defined in a normalized [0, 1] coordinate space, relative to the bounding box of the item being colored.

## Examples

```julia
gradient()
gradient(:red, :white, :blue)
```
