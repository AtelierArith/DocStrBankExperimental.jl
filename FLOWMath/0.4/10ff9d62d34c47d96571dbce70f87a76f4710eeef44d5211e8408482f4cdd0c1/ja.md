```
quintic_blend(fx::Tuple, xt::Tuple, x, delta_x)
```

`fx`内の関数の結果を五次多項式を使用して滑らかに遷移させ、`xt`内の位置で関数間の遷移を行います。`delta_x`はスムージング区間の半幅です。結果の関数はC2連続です。
