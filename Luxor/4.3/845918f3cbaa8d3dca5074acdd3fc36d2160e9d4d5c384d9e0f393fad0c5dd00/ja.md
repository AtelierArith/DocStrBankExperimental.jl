```
circlecircleoutertangents(cpt1::Point, r1, cpt2::Point, r2)
```

`p1`、`p2`、`p3`、`p4`の4つの点を返します。`p1`と`p2`を通る直線と、`p3`と`p4`を通る直線が、`cpt1/r1`および`cpt2/r2`で定義された円の外接接線を形成します。

一方の円が他方の円の内部にある場合、4つの同一の点（`O`）を返します。
