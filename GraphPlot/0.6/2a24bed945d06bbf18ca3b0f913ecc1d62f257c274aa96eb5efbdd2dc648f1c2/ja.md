この関数は [NetworkX](https://github.com/networkx/networkx) からのラップです。

グラフラプラシアンの固有ベクトルを使用してノードの位置を決定します。

**パラメータ**

*g* グラフ

*weight* 配列または何もない、オプション（デフォルト=nothing） エッジの重みとして使用される数値を保持するエッジ属性。 None の場合、すべてのエッジの重みは 1 になります。

**例**

```
julia> g = smallgraph(:karate)
julia> weight = rand(ne(g))
julia> locs_x, locs_y = spectral_layout(g, weight)
```
