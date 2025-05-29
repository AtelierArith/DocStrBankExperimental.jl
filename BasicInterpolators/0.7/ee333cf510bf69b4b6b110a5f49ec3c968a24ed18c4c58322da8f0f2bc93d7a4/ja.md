```
BilinearInterpolator(f, xa, xb, nx, ya, yb, ny, boundaries=StrictBoundaries())
```

関数 `f` のための `BilinearInterpolator` を構築します。最初の軸において [`xa`,`xb`] の範囲で `nx` 点を均等に配置し、第二の軸において [`ya`,`yb`] の範囲で `ny` 点を均等に配置します。
