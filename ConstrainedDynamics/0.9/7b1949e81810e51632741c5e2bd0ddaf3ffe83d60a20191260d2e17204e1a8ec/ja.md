```
setPosition!(mechanism, eqconstraint, xθ)
```

関節 `eqconstraint` の最小座標（ベクトル）を設定します。

回転関節の例:     setPosition!(mechanism, geteqconstraint(mechanism, "joint_name"), [pi/2])
