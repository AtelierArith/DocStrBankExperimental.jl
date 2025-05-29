```
setForce!(mechanism, eqconstraint, Fτ)
```

関節 `eqconstraint` の最小座標力（ベクトル）を設定します。

プリズマティックジョイントの例:     setVelocity!(mechanism, geteqconstraint(mechanism, jointid), [-1.0])
