```
textfit(str, bbox::BoundingBox, maxfontsize = 800;
     horizontalmargin=12,
     leading=100)
```

Fit the string `str` into the bounding box `bbox` by adjusting the font size and line breaks.

Instead of using the current font size, the largest possible value will be calculated. You can specify a size limit in `maxfontsize`, such that the text will never be larger than this value, although it may have to be smaller.

`horizontalmargin` is applied to each side.

Optionally, `leading` can be supplied, and this will be interpreted as a percentage of the final calculated font size. The default value is 110 (%).

The function returns a named tuple with information about the calculated values:

```julia
(fontsize = 37.6, linecount = 5, finalpos = Point(-117.43, 92.60)
```

!!! note
    This function is in need of improvement. It's quite difficult to find out the height of a line of text in a specific font. (Unless we import FreeType.) Suggestions for improvements welcome!

