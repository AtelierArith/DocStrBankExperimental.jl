```
compactnodes(fens::FENodeSet, connected::Vector{Bool})
```

有限要素ノードセットを、接続されていないノードを削除することで圧縮します。

`fens` = 有限要素ノードの配列 `connected` = 配列要素 `connected[j]` は、0（`j` が接続されていないノードの場合）または正の数（ノード `j` が少なくとも1つの有限要素によって他のノードに接続されている場合）です。

# 出力

`fens` = 新しい有限要素ノードのセット `new_numbering`= 新しい `fens` 配列の中で接続されたノードがどこにあるかを示す配列（またはノードが接続されていなかった場合は0）。例えば、ノード5が接続されていて、新しい配列では3番目のノードである場合、`new_numbering[5]` は3になります。

# 例

メッシュから削除したい有限要素に接続されていないノードがあるとしましょう：それを達成する方法は以下の通りです。

```
connected = findunconnnodes(fens, fes);
fens, new_numbering = compactnodes(fens, connected);
fes = renumberconn!(fes, new_numbering);
```

最後に、メッシュが有効であることを確認します：

```
validate_mesh(fens, fes);
```
