```
ngonwalls(n, walltype = InfiniteWall{2, Absorbing}; kwargs...)
```

`n` 角を持つ正多角形の領域を `walltype` 壁で構築します。サイズは、外接円の半径 `r` または多角形の面積 `A` をキーワード引数として指定することで提供できます。さらに `wallsize=0.05` のマージンを追加できます。
