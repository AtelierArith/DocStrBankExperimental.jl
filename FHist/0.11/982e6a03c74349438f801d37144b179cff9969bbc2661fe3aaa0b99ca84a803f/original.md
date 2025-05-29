```
function lookup(h::Hist3D, x, y, z)
```

For given x/y/z-axis value `x`, `y`, `z`, find the corresponding bin and return the bin content. If a value is out of the histogram range, return `missing`.
