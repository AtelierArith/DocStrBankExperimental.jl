```
has_marks(dg, v1, v2, t::Tuple{Symbol, Symbol}
```

ノード v1 と v2 の間のエッジがタプル t によって与えられたエッジマーカーを持っているかテストします（使用を簡素化するために矢印マクロを使用します）

例: `has_marks(dg, 1, 2, arrow"o->")`
