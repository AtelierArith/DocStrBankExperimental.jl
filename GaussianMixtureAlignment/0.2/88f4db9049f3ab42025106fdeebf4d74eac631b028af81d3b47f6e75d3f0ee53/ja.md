```
obj, pos = local_align(x, y, block, pσ=nothing, pϕ=nothing; R=nothing, T=nothing, maxevals=100)
```

指定された `block` 内でのローカルアラインメントを実行し、提供されたGMM `x` と `y` の目的関数 `objfun` を最小化するためにL-BFGSを使用します。
