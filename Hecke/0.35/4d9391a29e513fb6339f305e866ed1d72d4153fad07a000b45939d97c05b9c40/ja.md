```
rresx(f::PolyRingElem{ResElem{ZZRingElem}}, g::PolyRingElem{ResElem{ZZRingElem}}) -> r, u, v
```

縮小された結果 $r$ と多項式 $u$ および $v$ は、$r = uf+vg$ かつ $\langle r\rangle = \langle f, g\rangle\cap \mathbb Z$ を満たします。
