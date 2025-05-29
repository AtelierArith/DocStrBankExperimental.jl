```
DFSIterator
```

`DFSIterator`は、深さ優先探索を使用してグラフの頂点を反復処理するために使用されます。ソースノードは、オプションで`Int`または複数のソースを提供する場合にインデックス可能な配列のような型として供給されます。

# 例

```julia-repl
julia> g = smallgraph(:house)
{5, 6} 無向単純 Int64 グラフ

julia> for node in DFSIterator(g, 3)
           display(node)
       end
1
2
4
3
5
```
