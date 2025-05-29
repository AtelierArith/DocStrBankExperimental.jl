```
struct HyperRectangle{Dim, M, CRS}
```

3次元を超える次元への`Meshes`の拡張です。

この拡張は最小限であり、メソッドを実装せず、CRSとインターフェースを持ちません。

### フィールド

  * `min`: `NTuple`としてのHyperRectangleの最小座標。
  * `max`: `NTuple`としてのHyperRectangleの最大座標。
  * `vertices`: `[min, max]`、`Meshes`によって要求されます。

### コンストラクタ

```
HyperRectangle(min, max)
```
