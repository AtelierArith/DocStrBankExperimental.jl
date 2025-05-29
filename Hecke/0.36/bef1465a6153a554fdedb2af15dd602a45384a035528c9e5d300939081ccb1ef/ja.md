```
rresx(f::ZZPolyRingElem, g::ZZPolyRingElem) -> r, u, v
```

縮小された結果、すなわち $f$ と $g$ によって生成される理想の整数との交差の生成元。さらに、$r = uf + vg$ となる多項式 $u$ と $v$ があり、$\deg u < \deg g$ および $\deg v < \deg f$ です。
