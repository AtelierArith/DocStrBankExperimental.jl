```
getchild(edge)
getchild(node)
getchildren(node)
```

子ノード **node** を取得します。

  * `getchild`: `edge` の単一の子ノード、または `node` が単一の子を持つことを確認した後の `node` の子ノード。
  * `getchildren`: `node` のすべての子ノードのベクトル。

```
getchildedge(node)
```

`node` の単一の子 **edge**。単一の子であることを確認します。

*警告*: これらの関数は、`ischild1` フィールドを介して正しいエッジの方向に依存しています。

参照: [`getparent`](@ref), [`getpartneredge`](@ref), [`isparentof`](@ref), [`hassinglechild`](@ref)。
