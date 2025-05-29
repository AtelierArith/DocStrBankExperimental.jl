```
points_in_shape(Shape; resolution = 20, xres = resolution, yres = resolution,
         exclude_region = EmptyShape(region), kws...)
```

は `(x_vec, region_inds)` を返します。ここで `x_vec` は `Shape` を囲むボックスをカバーする点のベクトルであり、`region_inds` は `x_vec[region_inds]` が `Shape` に含まれる点であるような線形インデックスの配列です。3Dの場合は `yres` の代わりに `zres` を使用します。
