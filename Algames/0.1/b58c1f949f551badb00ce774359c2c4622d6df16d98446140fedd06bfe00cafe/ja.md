```
ControlBoundConstraint{P,M,T}
```

制御に関する線形境界制約

# コンストラクタ

```julia
ControlBoundConstraint(m; u_min, u_max)
```

境界のいずれかは±∞である可能性があります。境界は単一のスカラーとして指定することもでき、これによりすべての制御に境界が適用されます。
