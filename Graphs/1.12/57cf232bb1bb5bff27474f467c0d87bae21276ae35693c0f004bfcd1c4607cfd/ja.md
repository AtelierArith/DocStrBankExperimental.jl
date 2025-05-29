```
period(g)
```

強連結有向グラフのすべての頂点の（共通の）周期を返します。グラフが強連結でない場合はエラーをスローします。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> period(g)
3
```
