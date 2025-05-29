```
draw_yaxis(y::Real; opts...)
```

`draw_yaxis(y)` は原点から `(0,y)` までの細い矢印を描きます。

`draw_yaxis(y1,y2)` は `draw_yaxis(x1); draw_yaxis(x2)` と同等です。

y値が指定されていない場合、原点から `ylims()` によって返される値よりも10%大きい値までの矢印のペアを描きます。
