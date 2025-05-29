```
spacefilling(mol::UndirectedGraph; radii="van der Waals")
```

`mol`を三次元のスペースフィリング（カロッテ）モデルとして表現します。`mol`は、オングストローム単位で表された3D原子位置を持っている必要があります。（3D SDFファイルは、PubChemなどのサイトからダウンロードできます。）`radii`にサポートされている2つのオプションは、`"van der Waals"`と`"covalent"`です。前者は主族元素にのみ利用可能で、後者はすべての元素に利用可能です。

この関数を使用するには、Makie/GLMakie/CairoMakieファミリーのいずれかのバックエンドをロードする必要があります。
