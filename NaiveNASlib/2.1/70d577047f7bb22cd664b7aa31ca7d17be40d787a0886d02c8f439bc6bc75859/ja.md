```
Δsize!(s::AbstractΔSizeStrategy) 
Δsize!(utilityfun, s::AbstractΔSizeStrategy)
```

`s`がサイズに影響を与える可能性のあるすべての頂点のサイズを変更します。

引数`utilityfun`は、同じグラフ内の任意の頂点`vx`に対してベクトル`utility = utilityfun(vx)`を提供します。ここで、`utility[i] > utility[j]`は、出力ニューロンインデックス`i`が頂点`vx`に対して`j`よりも優先されるべきであることを示します。また、`vx`のすべてのニューロンのユーティリティとして使用されるスカラーを提供することもできます。提供されない場合は、[`defaultutility(vx)`](@ref)が使用されます。
