```
rich_club(g, k)
```

Return the non-normalised [rich-club coefficient](https://en.wikipedia.org/wiki/Rich-club_coefficient) of graph `g`, with degree cut-off `k`.

```jldoctest
julia> using Graphs

julia> g = star_graph(5)
{5, 4} undirected simple Int64 graph

julia> rich_club(g, 1)
0.4
```
