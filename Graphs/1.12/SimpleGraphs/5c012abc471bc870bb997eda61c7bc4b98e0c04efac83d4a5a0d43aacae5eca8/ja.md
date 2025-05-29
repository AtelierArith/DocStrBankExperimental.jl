```
static_fitness_model(m, fitness_out, fitness_in)
```

$$
|fitness\_out + fitness\_in|
$$

頂点と `m` 辺を持つランダム有向グラフを生成します。このとき、$Edge_{ij}$ の存在確率は $i ∝ fitness\_out$ および $j ∝ fitness\_in$ に比例します。

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNGシードを設定します。

### パフォーマンス

時間計算量は $\mathcal{O}(|V| + |E| \log |E|)$ です。

### 参考文献

  * Goh K-I, Kahng B, Kim D: スケールフリーネットワークにおける負荷分配の普遍的な挙動. Phys Rev Lett 87(27):278701, 2001.

## 例

```
julia> using Graphs

julia> g = static_fitness_model(6, [1, 0.2, 0.2, 0.2], [0.1, 0.1, 0.1, 0.9]; seed=123)
{4, 6} 有向単純 Int64 グラフ

julia> edges(g) |> collect
6-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 3
 Edge 2 => 4
 Edge 3 => 4
```
