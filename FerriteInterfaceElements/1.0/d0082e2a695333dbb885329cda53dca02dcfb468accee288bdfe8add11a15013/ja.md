```
InterfaceCell(here::AbstractCell, there::AbstractCell) <: AbstractCell
```

`InterfaceCell`は、2つの低次元セルに基づくセルで、2つのファセットを表します。2つの基底セルは同じタイプである必要があり、ノードの順序が一致する必要があります。例えば：

```
1---2 "here"
4---3 "there"
InterfaceCell(Line((1,2)), Line((4,3)))
```

# フィールド

  * `here::AbstractCell`: ファセット "here" を表すセル
  * `there::AbstractCell`: ファセット "there" を表すセル
  * `nodes`::NTuple: 適切な順序で全てのノードインデックスを含むタプル：頂点ノード "here"、頂点ノード "there"、ファセットノード "here"、...
