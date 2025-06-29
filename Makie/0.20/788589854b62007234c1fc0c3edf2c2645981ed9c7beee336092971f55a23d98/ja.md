```
FileIO.save(filename, scene; size = size(scene), pt_per_unit = 0.75, px_per_unit = 1.0)
```

指定されたファイル名と形式で `Scene` を保存します。

# サポートされている形式

  * `GLMakie`: `.png`
  * `CairoMakie`: `.svg`, `.pdf` および `.png`
  * `WGLMakie`: `.png`

# サポートされているキーワード引数

## すべてのバックエンド

  * `size`: 次元のない単位でのシーンの `(width::Int, height::Int)`。
  * `update`: 保存前に図を更新するかどうか。これにより、図のすべての軸の制限がリセットされます。デフォルトは `true` です。
  * `backend`: 保存に使用する `Makie` バックエンドを指定します。デフォルトは現在のバックエンドです。
  * その他のキーワードは画面に転送されます。

## CairoMakie

  * `pt_per_unit`: ベクタ形式にエクスポートする際の `pt` での1つのシーン単位のサイズ。
  * `px_per_unit`: ビットマップ形式にエクスポートする際の `px` での1つのシーン単位のサイズ。これにより、同じシーンを高解像度または低解像度でエクスポートするためのメカニズムが提供されます。
