```
draw_xaxis(x::Real; opts...)
```

`draw_xaxis(x)` は原点から `(x,0)` までの細い矢印を描きます。

`draw_xaxis(x1,x2)` は `draw_xaxis(x1); draw_xaxis(x2)` と同等です。

x値が指定されていない場合、原点から `xlims()` によって返される値の10%大きい値までの矢印のペアを描きます。
