```
export_scene(;scene, filename, kwargs...)
```

現在の視覚化のスクリーンショットを PNG ファイルとしてエクスポートします（`scene` は `render` の呼び出しの出力として保存されます）。ファイルは `filename` で指定されたパスに保存されます（`.png` 拡張子を含む）。キーワード引数は、対応する Makie の `save` メソッドに渡されます（詳細は VPL ドキュメントを参照してください）。
