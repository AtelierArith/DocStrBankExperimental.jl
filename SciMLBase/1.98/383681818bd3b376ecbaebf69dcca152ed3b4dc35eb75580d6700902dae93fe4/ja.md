```
DiffEqScalar(val[; update_func])
```

時間依存のスカラー/スケーリング演算子を表します。更新関数は `update_coefficients!` によって呼び出され、次のシグネチャを持つと仮定されます：

```
update_func(oldval,u,p,t) -> newval
```
