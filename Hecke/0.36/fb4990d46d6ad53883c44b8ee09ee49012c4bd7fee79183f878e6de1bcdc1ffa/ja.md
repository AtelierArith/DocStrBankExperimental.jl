```
hensel_lift(f::ZZPolyRingElem, g::ZZPolyRingElem, p::ZZRingElem, k::Int) -> (ZZPolyRingElem, ZZPolyRingElem)
```

与えられた $f$ と $g$ に対して、$g$ は $f \mod p$ の因子であり、$g$ と $f/g$ は互いに素である。$g$ の Hensel リフトを $p^k$ モジュロで計算する。
