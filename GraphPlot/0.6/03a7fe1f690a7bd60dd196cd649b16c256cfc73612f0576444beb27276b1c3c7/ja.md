この関数は [NetworkX](https://github.com/networkx/networkx) からのラップです。

ノードを円の上に配置します。

**パラメータ**

*g* グラフ

**戻り値**

*locs*x, locs*y* ノードの位置。任意の単位を使用できますが、いずれにせよ正規化されて中心に配置されます。

**例**

```
julia> g = smallgraph(:house)
julia> locs_x, locs_y = circular_layout(g)
```
