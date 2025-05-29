```
evaluate(pm, xp, yp, field_dofs)
```

  * position(pm.dim) : 評価する位置
  * field*dofs(pm.n*dofs) : カーネル表現における自由度。
  * field_value : フィールドの値

指定された自由度で位置でフィールドを評価します。
