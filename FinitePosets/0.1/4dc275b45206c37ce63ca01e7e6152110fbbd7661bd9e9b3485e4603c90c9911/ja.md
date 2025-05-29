`CPoset(covers::Vector{Tuple{Int,Int}})`

は、与えられた関係の推移的閉包を表す部分順序集合（poset）を作成します。この部分順序集合は `1:n` 上にあり、`n` は関係に現れる最大の数です。

```julia-repl
julia> CPoset([(6,2),(5,1)])
3,4
5<1
6<2
```
