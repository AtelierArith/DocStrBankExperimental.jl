```
setcolor(r, g, b)
setcolor(r, g, b, alpha)
setcolor(color)
setcolor(col::Colors.Colorant)
setcolor(sethue("red")..., .2)
```

Set the current color.

Examples:

```
setcolor(convert(Colors.HSV, Colors.RGB(0.5, 1, 1)))
setcolor(.2, .3, .4, .5)
setcolor(convert(Colors.HSV, Colors.RGB(0.5, 1, 1)))

for i in 1:15:360
   setcolor(convert(Colors.RGB, Colors.HSV(i, 1, 1)))
   ...
end
```

See also [`sethue`](@ref).
