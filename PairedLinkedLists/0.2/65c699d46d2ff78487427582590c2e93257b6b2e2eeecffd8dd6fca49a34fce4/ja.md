```
l = SkipList{::Type}(; sortedby=identity, skipfactor=2)
l = SkipList{::Type}(elts...; sortedby=identity, skipfactor=2)
```

指定された型のデータを含む[SkipNode](@ref)で構成された`SkipList`を作成します。

リストの先頭には「ダミー」ノード`head`があり、リストの末尾には「ダミー」ノード`tail`があります。

データ構造の最上位レベルの先頭にあるノードには`l.top`でアクセスできます。

リスト`l`の最初の「実際の」ノードには`l.head.next`または`head(l)`でアクセスできます。同様に、最後の「実際の」ノードには`l.tail.prev`または`tail(l)`でアクセスできます。

リストの`skipfactor`は、上のレベルによって「スキップ」されるノードの平均数を示します。

リストの順序は、`sortedby`という関数で指定できます。

[`PairedSkipList`](@ref)や[`SkipNode`](@ref)も参照してください。
