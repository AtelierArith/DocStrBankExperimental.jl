```
function lookup(h::Hist2D, x, y)
```

For given x-axis and y-axis value `x`, `y`, find the corresponding bin and return the bin content. If a value is out of the histogram range, return `missing`.
