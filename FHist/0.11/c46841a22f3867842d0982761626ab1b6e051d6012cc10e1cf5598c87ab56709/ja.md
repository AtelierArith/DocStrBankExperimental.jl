```
restrict(h::Hist1D, low=-Inf, high=Inf)
restrict(low=-Inf, high=Inf) = h::Hist1D -> restrict(h, low, high)
```

x軸が制限された新しいヒストグラムを返します。`restrict(h, 0, 3)`（または `h |> restrict(0, 3)`）は、ビンの中心が `[0, 3]`（含む）にある `h` のスライスを返します。
