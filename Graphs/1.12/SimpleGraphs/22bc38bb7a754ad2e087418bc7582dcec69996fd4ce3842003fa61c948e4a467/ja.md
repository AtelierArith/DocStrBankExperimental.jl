```
rem_edge!(g, e)
```

グラフ `g` からエッジ `e` を削除します。エッジが正常に削除された場合は `true` を返し、そうでない場合は `false` を返します。

### 実装ノート

`rem_edge!` が `false` を返す場合、関数が `false` で終了する可能性がある複数のポイントがあるため、グラフは不確定な状態にある可能性があります。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> rem_edge!(g, 1, 2)
true

julia> rem_edge!(g, 1, 2)
false
```
