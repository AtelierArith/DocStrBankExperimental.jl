```
viewfile(file)
viewfile(file, format)
```

ファイルから分子構造を表示します。ポップアップウィンドウまたはノートブックの出力セルに表示されます。引数はファイルパスとフォーマット（"pdb"、"sdf"、"xyz"または"mol2"）です。提供されない場合、フォーマットはファイル拡張子から推測されます。例えば、"myfile.xyz"はxyzフォーマットとして扱われます。オプションのキーワード引数は`style`、`surface`、`isosurface`、`box`、`lines`、`cylinders`、`vtkcell`、`axes`、`cameraangle`、`height`、`width`、`html`および`debug`です。
