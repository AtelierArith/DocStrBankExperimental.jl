```
rebin(h::Hist2D, nx::Int=1, ny::Int=nx)
rebin(nx::Int, ny::Int) = h::Hist2D -> rebin(h, nx, ny)
```

Merges `nx` (`ny`) consecutive bins into one along the x (y) axis by summing.
