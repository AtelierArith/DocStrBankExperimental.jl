```
GNNChain(layers...)
GNNChain(name = layer, ...)
```

複数のレイヤー/関数を収集し、与えられた入力グラフと入力ノード特徴に対して順次呼び出すことができます。

これは、`Lux.Chain`が行うように、各レイヤーの出力を次のレイヤーに伝播させる形でレイヤーを順次構成することを可能にします。さらに、`GNNChain`は入力グラフも処理し、[`GNNLayer`](@ref) 抽象型をサブタイプとするレイヤーにのみ最初の引数として提供します。

`GNNChain`はインデックス付けとスライスをサポートしており、`m[2]`や`m[1:end-1]`のように使用できます。また、名前が与えられた場合、`m[:name] == m[1]`などのようにアクセスできます。

# 例

```jldoctest
julia> using Lux, GNNLux, Random

julia> rng = Random.default_rng();

julia> m = GNNChain(GCNConv(2=>5), 
                    x -> relu.(x), 
                    Dense(5=>4))

julia> x = randn(rng, Float32, 2, 3);

julia> g = rand_graph(rng, 3, 6)
GNNGraph:
  num_nodes: 3
  num_edges: 6

julia> ps, st = LuxCore.setup(rng, m);

julia> m(g, x, ps, st)     # 最初のエントリは出力、2番目のエントリはモデルの状態
(Float32[-0.15594329 -0.15594329 -0.15594329; 0.93431795 0.93431795 0.93431795; 0.27568763 0.27568763 0.27568763; 0.12568939 0.12568939 0.12568939], (layer_1 = NamedTuple(), layer_2 = NamedTuple(), layer_3 = NamedTuple()))
```
