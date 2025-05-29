```
polyneigh(A, criterion = :Queen)
```

ジオメトリ列を含むテーブルAから空間重みオブジェクトを構築します。

# オプション引数

  * `criterion=:Queen`: 隣接基準。 `:Queen` または `:Rook`。
  * `tol=0.0`: ポリゴンの隣接性に対する許容誤差。
