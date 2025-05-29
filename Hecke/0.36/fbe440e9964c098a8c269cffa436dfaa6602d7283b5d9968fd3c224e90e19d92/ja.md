```
hensel_lift(f::ZZPolyRingElem, g::ZZPolyRingElem, h::ZZPolyRingElem, p::ZZRingElem, k::Int) -> (ZZPolyRingElem, ZZPolyRingElem)
```

与えられた $f = gh$ は $p$ に対して互いに素な $g, h$ の場合、$f = GH \mod p^k$ となるように $G, H$ を計算します。ここで、$G = g \mod p$ および $H = h \mod p$ です。
