```
text(str)
text(str, pos)
text(str, pos, angle = pi/2)
text(str, x, y)
text(str, pos, halign = :left)
text(str, valign = :baseline)
text(str, valign = :baseline, halign = :left)
text(str, pos, valign = :baseline, halign = :left)
text(latexstr, pos, valign = :baseline, halign = :left, rotationfixed = false, angle = 0)
text(typststr, pos::Point, place=true, centered=false, preamble=typststr)
```

Draw the text in the string `str` at `x`/`y` or `pt`, placing the start of the string at the point. If you omit the point, it's placed at the current `0/0`.

`angle` specifies the rotation of the text relative to the current x-axis.

Horizontal alignment `halign` can be `:left`, `:center`, (also `:centre`) or `:right`.  Vertical alignment `valign` can be `:baseline`, `:top`, `:middle`, or `:bottom`.

The default alignment is `:left`, `:baseline`.

This function uses Cairo's Toy text API.

Other text functions:

`textextents()` - find the dimensions of some text in the current font

`settext()` - like `text()` but using the Pro Api

`setfont()` - like `fontface()` but using the Pro Api

`label()` - draw text relative to a point with offset and leader lines

`textbox()` - draw an array of strings vertically downwards

`textcurve()` - draw text on a circular arc

`textfit()` - fit text into a BoundingBox by resizing it

`textlines()` - splits text into an array of strings so as to fit width

`textonpoly()` - draw text that sits on the edges of a polygon

`textpath()` - convert text to paths (straight lines and Bezier segments)

`textoutlines()` - Convert text to polygons (straight lines of varying lengths)

`textplace()` - draw text character by character with font/size/position specs

`texttrack()` - draw text tracked (tight or loose)

`textwrap()` - draw text to fit a box after re-justifying the lines to fit nicely
