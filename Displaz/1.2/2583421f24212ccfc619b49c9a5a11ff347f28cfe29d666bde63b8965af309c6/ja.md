```
annotation([plotobj::DisplazWindow,] coords::Array{T,1}, text::String, label=text::String)
```

指定された座標にテキスト注釈を配置します。

指定されていない場合、`plotobj`は現在のプロットウィンドウです。coordsは3要素の配列[x, y, z]で、textはプロットするテキストであり、Displazラベルのラベルです。注釈ラベルはDisplazのデータセットのリストには表示されませんが、注釈をアンロードするために必要です。指定されていない場合、ラベルは注釈文字列にデフォルト設定されます。
