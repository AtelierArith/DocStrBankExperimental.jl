```
draw_xtick(x::Real, len = _DEFAULT_TICK_LEN; opts...)
```

`draw_xtick(x::Real,len)` は、x軸に合計長さ `len` の目盛りを描画します。`len` が省略された場合は、`SimpleDrawing._DEFAULT_TICK_LEN` を使用します。

`draw_xtick(xlist,len)` は、`xlist` の各値に対して `draw_xtick` を呼び出します。
