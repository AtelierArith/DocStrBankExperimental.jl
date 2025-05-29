```
reflect_across_line(geom, dir; through_pt=nothing)
reflect_across_line(geom, p0, p1)
```

ジオメトリ `geom` のコピーを、線に対して反射させて返します。

線は、通過する2点 `p0` と `p1` によって指定されるか、または方向 `dir`（ベクトルまたはx軸との角度）と通過する点 `through_pt` によって指定されます。
