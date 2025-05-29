```
GNNChain(layers...)
GNNChain(name = layer, ...)

複数のレイヤー/関数を収集し、与えられた入力グラフと入力ノード特徴に対して順次呼び出すことができます。

これは、`Flux.Chain`が行うように、各レイヤーの出力を次のレイヤーに伝播させる形でレイヤーを順次構成することを可能にします。さらに、`GNNChain`は入力グラフも処理し、[`GNNLayer`](@ref) 抽象型をサブタイプ化したレイヤーにのみ最初の引数として提供します。

`GNNChain`はインデックス付けとスライスをサポートしており、`m[2]`や`m[1:end-1]`が可能で、名前が与えられた場合は、`m[:name] == m[1]`などが成り立ちます。

# 例

```

jldoctest julia> using Flux, GraphNeuralNetworks

julia> m = GNNChain(GCNConv(2=>5),                      BatchNorm(5),                      x -> relu.(x),                      Dense(5, 4)) GNNChain(GCNConv(2 => 5), BatchNorm(5), #7, Dense(5 => 4))

julia> x = randn(Float32, 2, 3);

julia> g = rand*graph(3, 6) GNNGraph:     num*nodes = 3     num_edges = 6

julia> m(g, x) 4×3 Matrix{Float32}:     -0.795592  -0.795592  -0.795592     -0.736409  -0.736409  -0.736409     0.994925   0.994925   0.994925     0.857549   0.857549   0.857549

julia> m2 = GNNChain(enc = m,                       dec = DotDecoder()) GNNChain(enc = GNNChain(GCNConv(2 => 5), BatchNorm(5), #7, Dense(5 => 4)), dec = DotDecoder())

julia> m2(g, x) 1×6 Matrix{Float32}:  2.90053  2.90053  2.90053  2.90053  2.90053  2.90053

julia> m2[:enc](g, x) == m(g, x) true ```
