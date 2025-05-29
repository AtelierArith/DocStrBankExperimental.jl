```
triangle(cx, cy, wx=1, wy=wx, ϕ=0, value::Number=1, param::Real=0.5)
triangle(center::NTuple{2,RealU}, width::NTuple{2,RealU}=(1,1), ϕ::RealU=0, v=1, param=0.5)
```

`Object{Triangle}`をパラメータから構築します。`param=0.5`で`width[1] == width[2]`の場合、これはx軸に沿って中心に配置された底辺`width[1]`の等辺三角形です。
