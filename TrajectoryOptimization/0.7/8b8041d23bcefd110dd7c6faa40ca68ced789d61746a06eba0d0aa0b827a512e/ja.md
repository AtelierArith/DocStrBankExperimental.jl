```
BoundConstraint{P,NM,T}
```

状態と制御に対する線形境界制約

# コンストラクタ

```julia
BoundConstraint(n, m; x_min, x_max, u_min, u_max)
```

境界のいずれかは±∞であることができます。境界は単一のスカラーとして指定することもでき、これによりすべての状態/制御に境界が適用されます。
