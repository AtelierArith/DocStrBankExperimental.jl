```
Rectangle <: Stencil

Rectangle(offsets::Tuple{Tuple}...)
Rectangle{O}()
```

任意の形状の長方形ステンシル。これらは中心点の周りのオフセットのタプルで指定され、各次元ごとに1つずつあります。
