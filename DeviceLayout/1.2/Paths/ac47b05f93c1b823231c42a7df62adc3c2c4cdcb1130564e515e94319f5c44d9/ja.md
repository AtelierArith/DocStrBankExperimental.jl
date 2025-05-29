```
pathlength_nearest(seg::Paths.Segment, pt::Point)
```

`seg`上の`s`を返します。これは`norm(seg(s) - pt)`を最小化します。

`s`は`zero(s)`と`pathlength(seg)`の間にあります。
