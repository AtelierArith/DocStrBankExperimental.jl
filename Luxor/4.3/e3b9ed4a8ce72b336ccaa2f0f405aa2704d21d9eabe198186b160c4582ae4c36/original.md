```
textpath(t)
```

Convert the text in string `t` to paths, adding them to the current path, for subsequent filling/stroking etc...

You can use `pathtopoly()` or `getpath()` or `getpathflat()` to convert the paths to polygons.

See also `textoutlines()`. `textpath()` retains Bezier curves, whereas `textoutlines()` returns flattened curves.
