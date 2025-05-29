```julia
struct LatticeReactionSystem{Q, R, S, T} <: ModelingToolkit.AbstractTimeDependentSystem
```

離散（格子）空間における化学反応の空間システムの表現。

# フィールド

  * `reactionsystem`: 各頂点内の（非空間的）反応システム。
  * `spatial_reactions`: 個々の頂点間で定義された空間反応。
  * `lattice`: （離散的な）空間システムが定義される格子。
  * `num_verts`: 頂点の数（コンパートメント）。
  * `num_edges`: 辺の数。
  * `num_species`: 種の数。
  * `spatial_species`: 空間的に移動可能な種のリスト。
  * `parameters`: 頂点と辺に関連する格子反応システムに関するすべてのパラメータ。
  * `vertex_parameters`: 頂点に結びついた値を持つパラメータ。例えば、システムの各頂点でユニークな値を持つ可能性があるもの。
  * `edge_parameters`: 辺（隣接）に結びついた値を持つパラメータ。例えば、システムの各辺でユニークな値を持つ可能性があるもの。
  * `edge_iterator`: 格子のすべての辺を反復するイテレータ。現在の形式は常に `Vector{Pair{Int64,Int64}}` です。しかし、将来的には異なるタイプの格子に対して異なるタイプが使用される可能性があります（例えば、直交グリッドの場合、各辺を列挙する必要は技術的にはありません）。

引数:

  * `rs`: 空間モデルに拡張される非空間的 [`ReactionSystem`](@ref) モデル。
  * `srs`: 空間反応のベクトル。これにより、種が空間的に移動する方法のルールが提供されます。
  * `lattice`: カルテジアン格子、マスクされた格子、またはグラフのいずれか。これは非空間モデルが拡張される離散空間を記述します。

キーワード引数:

  * `diagonal_connections = false`: カルテジアンおよびマスクされた格子にのみ関連します。`true` の場合、対角に隣接するコンパートメントは隣接と見なされ、これらの間の空間反応が可能です。

例:

```julia
# パッケージを取得します。
using Catalyst, OrdinaryDiffEqDefault
import CairoMakie

# `LatticeReactionSystem` モデルを作成します。
rs = @reaction_network begin
    (p,d), 0 <--> X
end
diffusion_rx = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rs, [diffusion_rx], lattice)

# モデルをシミュレートします（ODEとジャンプを使用）。
u0 = [:X => rand(5,5)]
tspan = (0.0, 1.0)
ps = [:p => 1.0, :d => 0.5, :D => 0.1]
oprob = ODEProblem(lrs, u0, tspan, ps)
osol = solve(oprob)

# 解のアニメーションをファイル "lattice_animation.mp4" に保存します。
lattice_animation(osol, :X, lrs, "lattice_animation.mp4")
```

ノート:

  * Catalystにおける空間モデリングはまだ進行中の作業であり、これに対するフィードバック（または貢献）は大いに歓迎されます。
  * `LatticeReactionSystem` は主に離散空間のシステムをモデル化することを目的としています。これを使用して連続空間システムをモデル化することは可能ですが、ユーザーが離散化（格子）を決定する必要があります。連続空間モデルのためのより良いサポートは進行中の作業です。
  * Catalystには空間モデリングに関する広範なドキュメントが含まれており、[こちら](https://docs.sciml.ai/Catalyst/stable/spatial_modelling/lattice_reaction_systems/)で見つけることができます。
