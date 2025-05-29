```
meander!(p::Path, endpoint::Point, len, nseg::Int, r, sty::Paths.Style = style1(p); offset = 0)
```

別のメンダー法で、これは現在の終点から `endpoint` まで Path `p` を拡張し、結果として最終的な総パス長が `len` になるようにします。

  * `nseg`: メンダー内のUターンの数は 2*nseg になります。
