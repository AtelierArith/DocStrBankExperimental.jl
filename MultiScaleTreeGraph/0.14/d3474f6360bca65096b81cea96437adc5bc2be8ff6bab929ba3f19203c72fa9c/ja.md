```
NodeMTG(link, symbol, index, scale)
MutableNodeMTG(link, symbol, index, scale)
```

# NodeMTG 構造体

前のノードへのリンク、ノードのシンボル、およびそのインデックスに関するデータを保持する MTG ノードを構築します。

# 注意

  * シンボルは、mtg ファイルから読み取った場合、`CLASSES` セクションの `SYMBOL` 列にリストされている可能な値と一致する必要があります。
  * インデックスは完全に自由であり、*e.g.* 分岐順序を追跡する方法として使用できます。

```julia
NodeMTG("<", "Leaf", 2, 0)
```
