```
l = PairedSkipList{::Type}(; sortedby=identity, skipfactor=2)
l = PairedSkipList{::Type}(elts...; sortedby=identity, skipfactor=2)
```

指定された型のデータを含むノードを持つ `PairedSkipList` を作成します。各ノードは、リストの `target` に属するノードへのインターノードリンクを持つことができます。

リストには、その長さ `len`、リストの先頭にある「ダミー」ノード `head`、リストの末尾にある「ダミー」ノード `tail` が含まれています。また、リストはその「ターゲット」リストへの参照も含んでいます。

リスト `l` の最初の「実際の」ノードには `l.head.next` でアクセスできます。同様に、最後の「実際の」ノードには `l.tail.prev` でアクセスできます。

リストの `skipfactor` は、上記のレベルによって「スキップ」されるノードの平均数を示します。

リストの順序は、関数 `sortedby` によって指定できます。

[`SkipList`](@ref) や [`PairedSkipNode`](@ref) も参照してください。
