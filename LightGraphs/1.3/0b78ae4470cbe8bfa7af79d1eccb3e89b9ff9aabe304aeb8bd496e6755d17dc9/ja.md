```
radiality_centrality(g)
```

グラフ `g` のすべての頂点に対する [ラジアリティ中心性](http://www.cbmc.it/fastcent/doc/Radiality.htm) を計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返します。

頂点 $u$ のラジアリティ中心性 $R_u$ は次のように定義されます：$R_u = \frac{D_g + 1 - \frac{\sum_{v∈V}d_{u,v}}{|V|-1}}{D_g}$

ここで、$D_g$ はグラフの直径、$d_{u,v}$ は $u$ から $v$ への最短経路の長さです。

### 参考文献

  * Brandes, U.: A faster algorithm for betweenness centrality. J Math Sociol 25 (2001) 163-177

# 例

```jldoctest
julia> using LightGraphs

julia> radiality_centrality(star_graph(4))
4-element Array{Float64,1}:
 1.0               
 0.6666666666666666
 0.6666666666666666
 0.6666666666666666

julia> radiality_centrality(path_graph(3))
3-element Array{Float64,1}:
 0.75
 1.0 
 0.75
```
