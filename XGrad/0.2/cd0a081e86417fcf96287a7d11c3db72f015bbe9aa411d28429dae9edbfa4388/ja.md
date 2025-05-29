```
df = xdiff(f; ctx=Dict(), inputs...)
```

スカラー値関数をその入力に関して微分し、導関数を返します。

```
loss(w, x, y) = sum(w * x .- y)
w = rand(2,3); x = rand(3,4); y = rand(2)
dloss = xdiff(loss; w=w, x=x, y=y)
val, dw, dx, dy = dloss(w, x, y)
```

より動的なAPIについては `xgrad()` を参照してください。
