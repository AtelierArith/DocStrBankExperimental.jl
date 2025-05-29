```
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], g::CompGraph)
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], v::AbstractVertex)
```

グラフ `g` の（潜在的に）すべての頂点のサイズを、提供された [`AbstractΔSizeStrategy`](@ref) （デフォルトは [`UpperInsertBound`](@ref)）に従って変更します。

操作が成功した場合は true を返し、そうでない場合は false を返します。

引数 `utilityfun` は、同じグラフ内の任意の頂点 `vx` に対してベクトル `utility = utilityfun(vx)` を提供します。ここで `utility[i] > utility[j]` は、出力ニューロンインデックス `i` が頂点 `vx` に対して `j` よりも優先されるべきであることを示します。また、`vx` のすべてのニューロンのユーティリティとして使用されるスカラーを提供することもできます。提供されない場合は、[`defaultutility(vx)`](@ref) が使用されます。
