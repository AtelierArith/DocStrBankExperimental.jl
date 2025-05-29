```
rich_club(g, k)
```

グラフ `g` の非正規化された [リッチクラブ係数](https://en.wikipedia.org/wiki/Rich-club_coefficient) を、次数カットオフ `k` で返します。

```jldoctest
julia> using Graphs

julia> g = star_graph(5)
{5, 4} undirected simple Int64 graph

julia> rich_club(g, 1)
0.4
```
