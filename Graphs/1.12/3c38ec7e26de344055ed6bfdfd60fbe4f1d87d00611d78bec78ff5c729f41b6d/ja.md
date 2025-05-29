```
savegraph(file, d, format=LGFormat())
```

辞書 `d` の `graphname => graph` を `file` に `format` 形式で保存します。書き込まれたグラフの数を返します。

# 例

```jldoctest
julia> using Graphs

julia> g1 = SimpleGraph(5,8)
{5, 8} 無向単純 Int64 グラフ

julia> g2 = SimpleGraph(7,10)
{7, 10} 無向単純 Int64 グラフ

julia> d = Dict("graph_1" => g1, "graph_2" => g2);

julia> savegraph("myfile.txt", d, LGFormat())
2
```

### 実装ノート

ファイル形式が複数のグラフタイプをサポートしている場合にのみ機能します。
