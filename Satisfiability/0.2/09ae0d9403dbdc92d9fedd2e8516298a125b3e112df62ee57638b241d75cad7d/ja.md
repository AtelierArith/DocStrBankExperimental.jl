```
iff(z1::BoolExpr, z2::BoolExpr)
z1 ⟺ z2
```

z1とz2の間の双方向の含意。`and(z1 ⟹ z2, z2 ⟹ z1)`と同等です。
