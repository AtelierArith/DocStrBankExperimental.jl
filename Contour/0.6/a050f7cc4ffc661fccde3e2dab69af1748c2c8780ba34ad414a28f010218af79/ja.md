```
contour(x, y, z, level::Number)
contour(x, y, z, level::Number, VT::Type)
```

引数 `level` で示される単一の等高線レベルを描画します。抽出された頂点の型は `VT` で指定できます。

通常、`contour` の出力に対して [`lines`](@ref) を呼び出し、その結果を反復処理します。
