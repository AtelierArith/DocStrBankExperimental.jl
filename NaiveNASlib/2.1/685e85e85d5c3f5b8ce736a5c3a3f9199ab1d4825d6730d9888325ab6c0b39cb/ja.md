```
Δsize!([utilityfun], [s::AbstractΔSizeStrategy], vs::AbstractVector{<:AbstractVertex})
```

提供された [`AbstractΔSizeStrategy`](@ref) に従って、`vs` 内の（潜在的に）すべての頂点のサイズを変更します（デフォルトは [`UpperInsertBound`](@ref)）。

引数 `utilityfun` は、同じグラフ内の任意の頂点 `vx` に対してベクトル `utility = utilityfun(vx)` を提供します。ここで `utility[i] > utility[j]` は、出力ニューロンインデックス `i` が頂点 `vx` に対して `j` よりも優先されるべきであることを示します。また、`vx` のすべてのニューロンのユーティリティとして使用されるスカラーを提供することもできます。提供されない場合は、[`defaultutility(vx)`](@ref) が使用されます。
