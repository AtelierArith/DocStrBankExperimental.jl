```
addstop(b::Blend, offset, col)
addstop(b::Blend, offset, (r, g, b, a))
addstop(b::Blend, offset, string)
```

Add a color stop to a blend. The offset specifies the location along the blend's 'control vector', which varies between 0 (beginning of the blend) and 1 (end of the blend). For linear blends, the control vector is from the start point to the end point. For radial blends, the control vector is from any point on the start circle, to the corresponding point on the end circle.

Examples:

```
blendredblue = blend(Point(0, 0), 0, Point(0, 0), 1)
addstop(blendredblue, 0, setcolor(sethue("red")..., .2))
addstop(blendredblue, 1, setcolor(sethue("blue")..., .2))
addstop(blendredblue, 0.5, sethue(randomhue()...))
addstop(blendredblue, 0.5, setcolor(randomcolor()...))
```
