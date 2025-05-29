```
function induced_subgraph(g::MetaGraphsNext.MetaGraph, vlist::Vector{String})
```

は、`vlist`のノード（または頂点）から`g`における誘導部分グラフを作成するために必要な部分*busses::Vector{String}および部分*edges::Vector{Tuple{String, String}}を返します。
