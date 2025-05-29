```
label(mat[, neighborhood = :rook])
```

同じ値を持つ隣接する行列要素のすべてのクラスターに任意のラベルを割り当てます。値の行列と最終的なクラスターの総数を返します。`neighborhood` 構造は `:rook` `:queen` `:diagonal` 0 1 0 1 1 1 0 1 1 1 x 1 1 x 1 1 x 1 0 1 0 1 1 1 1 1 0 であり、`:rook` がデフォルトです。
