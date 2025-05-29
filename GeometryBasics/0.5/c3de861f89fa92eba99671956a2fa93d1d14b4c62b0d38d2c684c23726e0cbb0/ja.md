```
MetaMesh(mesh; metadata...)
MetaMesh(positions, faces; metadata...)
```

`mesh`から別の`MetaMesh`を構築するか、与えられた`positions`と`faces`を使用して別のメッシュを構築します。与えられたキーワード引数はすべて`MetaMesh`の`meta`フィールドに保存されます。

この構造体は、非頂点データの保存に使用されることを意図しています。頂点に関連するデータは、`Mesh`の頂点属性として保存する必要があります。そのようなデータの一例は、`mesh.views`でビューごとに定義されるマテリアルデータです。つまり、サブメッシュごとです。

`MetaMesh`に追加されたメタデータは、Dictのような操作（getindex、setindex!、get、delete、keysなど）で操作できます。頂点属性にはフィールドとメッシュと同じゲッターを介してアクセスできます。メッシュ自体は`Mesh(metamesh)`で取得できます。
