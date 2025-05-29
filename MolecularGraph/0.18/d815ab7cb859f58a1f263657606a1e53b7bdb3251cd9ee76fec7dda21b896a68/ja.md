```
ballstick(mol::UndirectedGraph; radii=0.3, bonddiameter=0.1)
```

`mol`をボール・アンド・スティックモデルとして三次元で表現します。`mol`は、オングストローム単位で表された3D原子位置を持っている必要があります。3D SDFファイルは、PubChemなどのサイトからダウンロードできます。

`radii`はオプションで、ボールの半径をオングストローム単位で指定します。`bonddiameter`はオプションで、スティックの半径をオングストローム単位で指定します。

この関数を使用するには、Makie/GLMakie/CairoMakieファミリーのいずれかのバックエンドをロードする必要があります。
