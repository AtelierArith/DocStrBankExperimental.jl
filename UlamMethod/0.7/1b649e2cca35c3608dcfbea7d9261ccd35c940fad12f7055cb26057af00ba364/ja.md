```
struct Bins{Dim, M, CRS}
```

次元 `Dim` のビンを多様体 `M` に埋め込み、座標参照系 `CRS` を持つコンテナ型です。

### フィールド

  * `bins`: `Polytope{Dim, M, CRS}` オブジェクトのベクター。

### メソッド

```
points(bins)
```

各ビンの生の頂点のベクターを返します。
