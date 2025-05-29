```
beziersegments(paths::Vector{AbstractPath})
beziersegments!(sc, paths::Vector{AbstractPath})
```

ベジェパスを描画するためのレシピ。各パスは離散化され、別々の `lines` プロットで描画されます。スカラー属性はすべてのサブプロットに使用されます。パスと同じ長さのベクトル属性を提供すると、i 番目の `lines` サブプロットは i 番目の属性を参照します。

TODO: パスの数が変わるとベジェセグメントプロットは機能しません。
