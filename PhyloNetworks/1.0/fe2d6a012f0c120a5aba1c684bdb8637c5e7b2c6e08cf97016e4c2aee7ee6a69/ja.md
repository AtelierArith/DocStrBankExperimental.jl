```
getparent(edge)
getparent(node)
getparentminor(node)
getparents(node)
```

親の**ノード**を取得します。

  * `getparent`: `edge`または`node`の**主要**（または唯一の）親ノード
  * `getparentminor`: `node`のマイナー親ノード
  * `getparents`: `node`のすべての親ノードのベクトル。

```
getparentedge(node)
getparentedgeminor(node)
```

`node`の親の**エッジ**を1つ取得します。

  * `getparentedge`: 主要な親エッジ。ツリーノードの場合、それは唯一の親エッジです。
  * `getparentedgeminor`: マイナー親エッジ。`node`がハイブリッドの場合（`node`にマイナー親がない場合はエラー）。

`node`に複数の主要（またはマイナー）親エッジがある場合、最初のものが警告やエラーなしに返されます。

*警告*: これらの関数はエッジのフィールド`ischild1`を使用します。

参照: [`getchild`](@ref), [`getpartneredge`](@ref).
