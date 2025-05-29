関数の勾配を指定された入力で計算し、導関数をキャッシュします。

```
loss(w, x, y) = sum(w * x .- y)
val, dw, dx, dy = xgrad(loss; w=rand(2,3), x=rand(3,4), y=rand(2))
```

`xgrad` はコンテキスト `ctx::Dict{}` とキャッシュ `mem::Dict{Any,Any}` も受け入れます。

関連情報: `xdiff`。
