```
ScalarFieldSequence(t::AbstractVector,s)
```

この型は、時間ベクトル `t` と補間可能なスカラー場のベクトル `s`（すなわち、各要素は2つの空間座標引数を持つ `AbstractInterpolation` 型）を束ねます。これは、軌跡に沿った場をプロットするために使用されます。
