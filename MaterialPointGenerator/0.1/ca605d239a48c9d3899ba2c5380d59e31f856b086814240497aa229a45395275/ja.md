```
getnormals(points::AbstractMatrix{T}; k::Integer=10)
```

## 説明:

k近傍法を使用して点の外法線を計算します。

  * 入力点は `N×3` 配列である必要があります。
  * 出力法線は `N×3` 配列になります。
