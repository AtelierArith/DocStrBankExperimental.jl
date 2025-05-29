```
draw_ytick(y::Real, len = _DEFAULT_TICK_LEN; opts...)
```

`draw_ytick(y::Real,len)` は、y軸に合計長さ `len` の目盛りを描画します。`len` が省略された場合は、`SimpleDrawing._DEFAULT_TICK_LEN` を使用します。

`draw_xtick(ylist,len)` は、`xyist` の各値に対して `draw_ytick` を呼び出します。
