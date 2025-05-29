```
static_fitness_model(m, fitness)
```

$$
|fitness|
$$

頂点と `m` 辺を持つランダムグラフを生成します。このとき、$Edge_{ij}$ の存在確率は $fitness_i × fitness_j$ に比例します。

### オプション引数

  * `seed=-1`: RNG シードを設定します。

### パフォーマンス

時間計算量は $\mathcal{O}(|V| + |E| \log |E|)$ です。

### 参考文献

  * Goh K-I, Kahng B, Kim D: スケールフリーネットワークにおける負荷分配の普遍的な挙動. Phys Rev Lett 87(27):278701, 2001.

## 例

```jldoctest
julia> g = static_fitness_model(5, [1, 1, 0.5, 0.1])
{4, 5} 無向単純 Int64 グラフ

julia> edges(g) |> collect
5-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 3
 Edge 2 => 4
```
