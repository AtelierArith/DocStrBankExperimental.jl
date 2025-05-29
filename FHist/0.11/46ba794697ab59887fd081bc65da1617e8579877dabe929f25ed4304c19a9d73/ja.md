```
restrict(h::Hist2D, xlow=-Inf, xhigh=Inf, ylow=-Inf, yhigh=Inf)
restrict(xlow=-Inf, xhigh=Inf, ylow=-Inf, yhigh=Inf) = h::Hist2D -> restrict(h, xlow, xhigh, ylow, yhigh)
```

新しいヒストグラムを制限されたx軸で返します。 `restrict(h, 0, 3)`（または `h |> restrict(0, 3)`）は、ビンの中心が `[0, 3]`（含む）にある `h` のスライスを返します。
