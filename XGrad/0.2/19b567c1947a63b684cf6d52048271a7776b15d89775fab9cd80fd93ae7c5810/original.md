Calculate gradient of a function at specified inputs, cache the derivative.

```
loss(w, x, y) = sum(w * x .- y)
val, dw, dx, dy = xgrad(loss; w=rand(2,3), x=rand(3,4), y=rand(2))
```

`xgrad` also accepts context `ctx::Dict{}` and cache `mem::Dict{Any,Any}`.

See also: `xdiff`.
