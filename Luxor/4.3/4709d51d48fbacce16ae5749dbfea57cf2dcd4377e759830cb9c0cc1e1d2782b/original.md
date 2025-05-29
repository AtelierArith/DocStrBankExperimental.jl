```
textonpoly(str, pgon;
        tracking = 0,
        startoffset = 0.0,
        baselineshift = 0.0,
        closed = false)
```

Draw the text in `str` along the route of the polygon in `pgon`.

The `closed` option determines whether the final edge of the polygon (joining the last point to the first) is included or not. Eg if you want to draw a string around all three sides of a triangle, you'd use `closed=true`:

```julia
textonpoly("mèdeis ageômetrètos eisitô mou tèn
stegèn - let no one ignorant of geometry come under my roof
",
    ngon(O, 100, 3, vertices=true),
    closed=true)
```

If `false`, only two sides are considered.

Increase `tracking` from 0 to add space between the glyphs.

The `startoffset` value is a normalized percentage that specifies the start position. So, to start drawing the text halfway along the polygon, specify a start offset value of 0.5.

Positive values for `baselineshift` move the characters upwards from the baseline.

Returns a tuple with the number of characters drawn, and the final value of the index, between 0.0 and 1.0. If the returned index value is less than 1, this means that the text supplied ran out before the end of the polygon was reached.
