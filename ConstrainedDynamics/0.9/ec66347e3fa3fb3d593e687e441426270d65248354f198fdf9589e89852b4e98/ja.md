```
setVelocity!(mechanism, eqconstraint, vω)
```

関節 `eqconstraint` の最小座標速度（ベクトル）を設定します。

平面関節の例:     setVelocity!(mechanism, geteqconstraint(mechanism, jointid), [0.5;2.0])
