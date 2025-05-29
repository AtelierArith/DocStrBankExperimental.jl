```
ll = logsumexp!(w, we [, maxw])
```

重みベクトル `w` を正規化し、加重対数尤度を返します。

https://arxiv.org/pdf/1412.8695.pdf eq 3.8 for p(y) https://discourse.julialang.org/t/fast-logsumexp/22827/7?u=baggepinnen for stable logsumexp
