```
rebin(h::Hist1D, n::Int=1)
rebin(n::Int) = h::Hist1D -> rebin(h, n)
```

Merges `n` consecutive bins into one. The returned histogram will have `nbins(h)/n` bins.
