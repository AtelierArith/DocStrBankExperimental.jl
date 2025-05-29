```
TwoPointFiniteVolumeGeometry(neighbors, areas, volumes, normals, cell_centers, face_centers)
```

与えられた `neighbors` のリストのために二点幾何情報を格納します。`neighbors` は `2` by `n` 行列として指定され、ここで `n` は面の数であり、面 `i` はセル `N[1, i]` と `N[2, i]` を接続します。

二点有限体積幾何は、標準的な有限体積離散化を計算するために必要な最小限の幾何情報を含んでいます。
