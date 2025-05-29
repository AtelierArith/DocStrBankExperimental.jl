```
StateBoundConstraint{P,N,T}
```

状態に対する線形境界制約

# コンストラクタ

```julia
StateBoundConstraint(n; x_min, x_max)
```

境界のいずれかは±∞である可能性があります。境界は単一のスカラーとして指定することもでき、これによりすべての状態に境界が適用されます。
