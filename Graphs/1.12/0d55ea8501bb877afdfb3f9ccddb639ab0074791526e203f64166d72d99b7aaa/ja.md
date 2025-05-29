```
sum(g, i)
```

グラフ `g` の入次数 (`i`=1) または出次数 (`i`=2) の値のベクトルを返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> sum(g, 2)
5-element Vector{Int64}:
 1
 1
 2
 1
 1

julia> sum(g, 1)
5-element Vector{Int64}:
 1
 1
 1
 2
 1
```
