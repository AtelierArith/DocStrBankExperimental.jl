```
find_binary(root::T, bin::String)::T where T<:AbstractNode
```

バイナリ表現によってノードを見つけます。この関数は、ノードがツリーに存在することを前提としています。

ノードがツリーに存在するかどうか不明な場合は、この関数を使用しないでください。

目的のノードへの参照を返します。

  * `root` : 検索するツリーのルートノード。
  * `bin` : 目的のノードのバイナリ表現（文字列として）。
