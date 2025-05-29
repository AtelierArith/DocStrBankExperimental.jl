```
box(pt, width, height, cornerradii::Array; action=:none)
box(pt, width, height, cornerradii::Array, action=:none)
```

Draw a box/rectangle centered at point `pt` with `width` and `height` and round each corner by the corresponding value in the array `cornerradii`.

The constructed path consists of arcs and straight lines.

The first corner is the one at the bottom left, the second at the top left, and so on.

## Example

```julia
@draw begin
    box(O, 120, 120, [0, 20, 40, 60], :fill)
end
```
