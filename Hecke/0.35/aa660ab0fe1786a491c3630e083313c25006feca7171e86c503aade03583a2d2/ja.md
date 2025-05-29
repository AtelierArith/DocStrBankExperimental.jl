```
hnf_extend!(A::SMat{ZZRingElem}, b::SMat{ZZRingElem}, offset::Int = 0) -> SMat{ZZRingElem}
```

与えられた行列 $A$ が HNF の場合、これを拡張して $b$ との連結の HNF を取得します。
