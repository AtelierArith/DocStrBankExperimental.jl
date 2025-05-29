```
rebin(h::Hist2D, nx::Int=1, ny::Int=nx)
rebin(nx::Int, ny::Int) = h::Hist2D -> rebin(h, nx, ny)
```

`nx`（`ny`）個の連続したビンをx（y）軸に沿って合計して1つにマージします。
