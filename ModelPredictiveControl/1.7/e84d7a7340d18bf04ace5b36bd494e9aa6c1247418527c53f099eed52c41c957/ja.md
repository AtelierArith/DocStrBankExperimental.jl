```
LinModel(sys::DelayLtiSystem, Ts; i_u=1:size(sys,2), i_d=Int[])
```

遅延のある連続システム `sys` をゼロオーダーホールドで離散化します。

遅延はサンプル時間 `Ts` の倍数でなければなりません。
