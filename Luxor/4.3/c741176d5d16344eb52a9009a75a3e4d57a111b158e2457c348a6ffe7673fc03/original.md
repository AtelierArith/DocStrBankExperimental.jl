```
image_as_matrix()
```

Return an Array of the current state of the picture as an array of ARGB32.

A matrix 50 wide and 30 high => a table 30 rows by 50 cols

```julia
using Luxor, Images

Drawing(50, 50, :png)
origin()
background(randomhue()...)
sethue("white")
fontsize(40)
fontface("Georgia")
text("42", halign=:center, valign=:middle)
mat = image_as_matrix()
finish()
```
