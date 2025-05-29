```
euclidean_graph(points)
```

`d×N` 行列 `points` を与えると、`N` 頂点のユークリッドグラフを構築し、グラフと各エッジの距離を含む Dict を返します。

### オプション引数

  * `L=1`: 点が選択される `d` 次元ボックスの境界を設定するために使用されます。
  * `p=2`
  * `bc=:open`

### 実装ノート

`d` 次元ベクトル `x[i] = points[:,i]` を定義し、頂点 `i` と `j` の間にエッジが挿入されるのは、`norm(x[i]-x[j], p) < cutoff` の場合です。`cutoff` が負の場合は、すべてのエッジが挿入されます。`p=2` の場合、標準的なユークリッド距離になります。ボックス $[0,L]^d$ に周期境界条件を課すには、`bc=:periodic` を設定します。

## 例

```jldoctest
julia> pts = rand(3, 10); # R^3 の 10 頂点

julia> g, dists = euclidean_graph(pts, p=1, bc=:periodic) # タクシー距離 (L^1);

julia> g
{10, 45} 無向単純 Int64 グラフ
```
