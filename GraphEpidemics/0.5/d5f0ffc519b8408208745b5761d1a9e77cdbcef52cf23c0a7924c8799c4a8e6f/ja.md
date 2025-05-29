`init_model_discrete(model::AbstractEpiModel, g::AbstractGraph, nodes_active::Vector{I}, init_state_inactive::Symbol, init_state_active::Symbol, rng::AbstractRNG) where I <: Integer`

シミュレーション状態を初期化し、一部のノードがアクティブに感染し、他のノードは非アクティブになります。

グラフ `g` はノード構造を提供します。`nodes_active` にあるノードには `init_state_active` が割り当てられ、他のすべてのノードには `init_state_inactive` が割り当てられます。遅延値と感染メタデータはそれに応じて初期化されます。
