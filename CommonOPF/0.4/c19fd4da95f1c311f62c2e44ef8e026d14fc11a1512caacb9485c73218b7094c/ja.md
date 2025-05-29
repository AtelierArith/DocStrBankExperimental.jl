```
all_inneighbors(g::MetaGraphsNext.MetaGraph, j::String, innies::Vector{String})
```

バス `j` の上にあるすべてのバスを見つけるための再帰関数。使用方法は次のとおりです：

```
busses_above_j = all_inneighbors(g, j, Vector{String}())
```
