```
map_from_canonical!(x, ξ, xmin, xmax, basis::NodalBasis{Line})
```

与えられた標準座標 `ξ` を区間 [-1, 1] から対応する座標 `x` にマッピングし、区間 [`xmin`, `xmax`] で `x` を更新します。
