```
binedges(h)
```

Get the bin edges of the histogram

!!! note
    For 1D histogram, it returns just a vector. For others, it returns a tuple of vectors. If you need a tuple of vectors, use `h.binedges` at your own risk.

