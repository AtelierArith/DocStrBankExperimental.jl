```
propagate(fmsg, g, aggr; [xi, xj, e])
propagate(fmsg, g, aggr xi, xj, e=nothing)
```

グラフ `g` 上でメッセージパッシングを実行します。各エッジ上のノード特徴を具現化し、メッセージ関数 `fmsg` を適用し、集約されたメッセージ $\bar{\mathbf{m}}$ を返します（`fmsg` の戻り値に応じて、配列または配列の名前付きタプルで、最後の次元のサイズは `g.num_nodes` です）。

これは二つのステップに分解できます：

```julia
m = apply_edges(fmsg, g, xi, xj, e)
m̄ = aggregate_neighbors(g, aggr, m)
```

GNN層は通常、フォワードパスで `propagate` を呼び出し、入力 `f` にクロージャを提供します。  

# 引数

  * `g`: `GNNGraph`。
  * `xi`: 最後の次元のサイズが `g.num_nodes` である配列または配列の名前付きタプル。各エッジのターゲットノードで適切に具現化されます（[`edge_index`](@ref GNNGraphs.edge_index) も参照）。
  * `xj`: `xj` と同様ですが、エッジのソースで具現化されます。
  * `e`: 最後の次元のサイズが `g.num_edges` である配列または配列の名前付きタプル。
  * `fmsg`: [`apply_edges`](@ref) に渡される汎用関数。エッジ具現化された `xi`、`xj`、および `e`（エッジのバッチサイズと同じサイズの配列または配列の名前付きタプル）を入力として受け取る必要があります。出力は同じバッチサイズの配列または配列の名前付きタプルでなければなりません。また、`layer` が `propagate` に渡される場合、`fmsg` のシグネチャは `fmsg(layer, xi, xj, e)` でなければなりません。
  * `aggr`: 隣接集約演算子。`+`、`mean`、`max`、または `min` を使用します。

# 例

```julia
using GraphNeuralNetworks, Flux

struct GNNConv <: GNNLayer
    W
    b
    σ
end

Flux.@layer GNNConv

function GNNConv(ch::Pair{Int,Int}, σ=identity)
    in, out = ch
    W = Flux.glorot_uniform(out, in)
    b = zeros(Float32, out)
    GNNConv(W, b, σ)
end

function (l::GNNConv)(g::GNNGraph, x::AbstractMatrix)
    message(xi, xj, e) = l.W * xj
    m̄ = propagate(message, g, +, xj=x)
    return l.σ.(m̄ .+ l.bias)
end

l = GNNConv(10 => 20)
l(g, x)
```

[`apply_edges`](@ref) および [`aggregate_neighbors`](@ref) も参照してください。
