```
checkerboard!(c::Cell{T,S}, pixsize, rows::Integer, alt, meta::Meta=GDSMeta()) where {T,S}
```

セル `c` に、コントラスト曲線測定やPECの基準線量を得るために適したチェッカーボードパターンを生成します。

  * `pixsize`: 正方形の一辺の長さ
  * `rows`: 行数 == 列数
  * `alt`: `Point(zero(T), zero(T))` に最も近い正方形が塗りつぶされる（塗りつぶされない）場合は `false`（`true`）。これを使用して、チェッカーボードの完全なタイルを作成します。
