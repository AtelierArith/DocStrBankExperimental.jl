```
pathtobezierpaths(
    ; flat=true)
```

Convert the current Cairo path (which may consist of one or more paths) to an array of Bézier paths, each of which is an array of BezierPathSegments. Each path segment is a tuple of four points. A straight line is converted to a Bézier segment in which the control points are set to be the same as the end points.

If `flat` is true, use `getpathflat()` rather than `getpath()`.

# Example

This code draws the BezierPathSegments and shows the control points as "handles", like a vector-editing program might.

```julia
@svg begin
    fontface("MyanmarMN-Bold")
    st = "goo"
    thefontsize = 100
    fontsize(thefontsize)
    sethue("red")
    fontsize(thefontsize)
    textpath(st)
    nbps = pathtobezierpaths()
    for nbp in nbps
        setline(.15)
        sethue("grey50")
        drawbezierpath(nbp, :stroke)
        for p in nbp
            sethue("red")
            circle(p[2], 0.16, :fill)
            circle(p[3], 0.16, :fill)
            line(p[2], p[1], :stroke)
            line(p[3], p[4], :stroke)
            if p[1] != p[4]
                sethue("black")
                circle(p[1], 0.26, :fill)
                circle(p[4], 0.26, :fill)
            end
        end
    end
end
```
