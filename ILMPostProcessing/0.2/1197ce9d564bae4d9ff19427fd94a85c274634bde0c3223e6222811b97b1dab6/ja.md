```
VectorFieldSequence(t::AbstractVector,v)
```

この型は、時間ベクトル `t` と、補間可能なフィールドのタプルのベクトル `v` を束ねます（すなわち、タプルの各メンバーは、2つの空間座標引数を持つ `AbstractInterpolation` 型です）。これは、軌道計算や軌道に沿ったフィールドのプロットに使用されます。
