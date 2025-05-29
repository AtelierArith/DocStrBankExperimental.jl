単位球上の半径関数 r = f(x,y,z) のグラフのメッシュ。

```
polar((x,y,z)->cos(x*y*z+1.0), 200, field=DistField())
```
