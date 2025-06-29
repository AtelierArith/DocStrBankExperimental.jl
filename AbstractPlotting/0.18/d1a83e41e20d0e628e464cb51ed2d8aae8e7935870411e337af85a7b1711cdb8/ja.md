```
FileIO.save(filename, scene; resolution = size(scene), pt_per_unit = 0.75, px_per_unit = 1.0)
```

指定されたファイル名と形式で `Scene` を保存します。

# サポートされている形式

  * `GLMakie`: `.png`、`.jpeg`、および `.bmp`
  * `CairoMakie`: `.svg`、`.pdf`、`.png`、および `.jpeg`
  * `WGLMakie`: `.png`

# サポートされているキーワード引数

## すべてのバックエンド

  * `resolution`: 次元のない単位でのシーンの `(width::Int, height::Int)` （GLMakie および WGLMakie の `px` に相当）。

## CairoMakie

  * `pt_per_unit`: ベクタ形式にエクスポートする際の `pt` での1つのシーンユニットのサイズ。
  * `px_per_unit`: ビットマップ形式にエクスポートする際の `px` での1つのシーンユニットのサイズ。これにより、同じシーンをより高いまたは低い解像度でエクスポートするためのメカニズムが提供されます。
