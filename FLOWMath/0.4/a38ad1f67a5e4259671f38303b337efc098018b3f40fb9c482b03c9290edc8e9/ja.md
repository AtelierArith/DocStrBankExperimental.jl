```
cubic_blend(fx::Tuple, xt::Tuple, x, delta_x)
```

`fx`内の関数の結果を、`xt`の位置での関数間の遷移を用いて、三次多項式を使って滑らかに遷移させます。`delta_x`はスムージング区間の半幅です。結果の関数はC1連続です。
