```
meander!(p::Path, endpoint::Point, len, nseg::Int, r, sty::Paths.Style = style1(p); offset = 0)
```

Another meander method, this one extends Path `p` from its current end-point to meet `endpoint`, such that the resulting final total path length will be `len`.

  * `nseg`: the number of U-turns in the meander will be 2*nseg
