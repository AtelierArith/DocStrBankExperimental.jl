```
rebin(h::Hist1D, n::Int=1)
rebin(n::Int) = h::Hist1D -> rebin(h, n)
```

`n` 個の連続したビンを1つにマージします。返されるヒストグラムは `nbins(h)/n` ビンを持ちます。
