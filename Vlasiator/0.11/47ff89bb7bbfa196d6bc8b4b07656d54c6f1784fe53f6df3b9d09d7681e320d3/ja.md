```
viz(meta, var; args)
```

`meta`内の`var`のVlasiator出力をさまざまなオプションで視覚化します：

## キーワード引数

  * `axisunit`   - `AxisUnit`型の軸の単位
  * `colorscale` - `ColorScale`型のカラーマップのスケール
  * `normal`     - スライスの法線方向
  * `vmin`       - 最小カラー値
  * `vmax`       - 最大カラー値
  * `comp`       - ベクトル成分の選択

### 注意事項

  * この関数は、Julia v1.9以降の言語のパッケージ拡張を介してMakie.jlバックエンドが存在する場合にのみ機能します。
