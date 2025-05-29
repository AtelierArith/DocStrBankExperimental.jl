```
d = sdf(body::AbstractParametricBody,x,t)
```

`x`から時刻`t`における`body.curve`上の最も近い点までの符号付き距離。符号はパラメトリック曲線の巻き方向に依存します。
