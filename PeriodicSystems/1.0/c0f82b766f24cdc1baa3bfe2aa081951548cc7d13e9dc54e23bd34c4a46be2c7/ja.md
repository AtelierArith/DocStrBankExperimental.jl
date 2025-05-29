```
psteval(psys,tval) -> sys::DescriptorStateSpace
```

周期的システム `psys = (A(t),B(t),C(t),D(t))` と時間値 `tval` に対して、LTIシステム `sys = (A(tval),B(tval),C(tval),D(tval))` を計算します。もし `A(tval)` が正方行列でない場合、`A(tval)` は正方行列を形成するためにゼロでパディングされ、適切な数のゼロ行とゼロ列がそれぞれ `B(tval)` と `C(tval)` に追加されます。
