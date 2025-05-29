```
viewstruc(struc)
viewstruc(struc, atom_selectors...)
```

BioStructures.jlから構造要素を表示します。ポップアップウィンドウまたはノートブックの出力セルに表示されます。引数は`StructuralElementOrList`と、原子セレクタとして機能する0個以上の関数です - 詳細はBioStructures.jlのドキュメントを参照してください。オプションのキーワード引数は`style`、`surface`、`isosurface`、`box`、`lines`、`cylinders`、`vtkcell`、`axes`、`cameraangle`、`height`、`width`、`html`および`debug`です。
