```
scale!(t::Transformable, x, y)
scale!(t::Transformable, x, y, z)
scale!(t::Transformable, xyz)
scale!(t::Transformable, xyz...)
```

与えられた引数に基づいて、指定された `Transformable`（シーンまたはプロット）をスケーリングします。`x, y` または `x, y, z` を取ることができます。これは絶対スケーリングであり、相対スケーリングを行うオプションはありません。
