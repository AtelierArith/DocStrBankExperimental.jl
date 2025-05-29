```
toggle(condition,a,b)
```

`condition ? a : b` の型安定な同等物。 `promote_type(typeof(a),typeof(b))` に変換された値を返します。
