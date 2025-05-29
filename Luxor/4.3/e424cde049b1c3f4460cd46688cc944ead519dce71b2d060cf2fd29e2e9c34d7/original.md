```
dimension(p1::Point, p2::Point;
    format::Function   = (d) -> string(d), # process the measured value into a string
    offset             = 0.0,              # left/right, parallel with x axis
    fromextension      = (10.0, 10.0),     # length of extensions lines left and right
    toextension        = (10.0, 10.0),     #
    textverticaloffset = 0.0,              # range 1.0 (top) to -1.0 (bottom)
    texthorizontaloffset = 0.0,            # range 1.0 (top) to -1.0 (bottom)
    textgap            = 5,                # gap between start of each arrow (≈ fontsize?)
    textrotation       = 0.0,
    arrowlinewidth     = 1.0,
    arrowheadlength    = 10,
    arrowheadangle     = π/8)
```

Calculate and draw dimensioning graphics for the distance between `p1` and `p2`. The value can be formatted with function `format`.

`p1` is the lower on the page (ie probably the higher y value) point, `p2` is the higher on the page (ie probably lower y) point.

`offset` is to the left (-x) when negative.

Dimension graphics will be rotated to align with a line between `p1` and `p2`.

In `textverticaloffset`, "vertical" and "horizontal" are best understood by "looking" along the line from the first point to the second. `textverticaloffset` ranges from -1 to 1, `texthorizontaloffset` in default units.

```
        toextension
        [5  ,  5]
       <---> <--->
                             to
       -----------            +
            ^
            |

           -50

            |
            v
       ----------            +
                            from
       <---> <--->
         [5 , 5]
       fromextension

            <---------------->
                  offset
```

Returns the measured distance and the text.
