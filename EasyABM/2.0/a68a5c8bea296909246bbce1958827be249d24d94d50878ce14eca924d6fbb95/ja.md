```julia
create_graph_model(
    agents::Array{EasyABM.GraphAgent{A<:EasyABM.MType, B<:EasyABM.MType}, 1},
    graph::EasyABM.AbstractPropGraph{S<:EasyABM.MType, G<:EasyABM.GType};
    agents_type,
    graphics,
    random_positions,
    vis_space,
    kwargs...
) -> Union{Nothing, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.DirGType} where S<:EasyABM.MType, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.SimGType} where S<:EasyABM.MType}

```

モデルを作成します

  * `agents` : エージェントのリスト。
  * `graph`  : Graphs.jlで作成され、EasyABMグラフタイプに変換されたグラフ、またはEasyABMグラフ機能を使用して直接作成されたもの。
  * `graphics` : trueの場合、pos、shape、color、orientationのプロパティがデフォルトで各エージェントに割り当てられます。ユーザーによってすでに割り当てられていない場合。
  * `agents_type` : モデル実行中にエージェントの数が固定されている場合はStaticに設定します。そうでない場合はMortalに設定します。
  * `random_positions` : このプロパティがtrueの場合、各エージェントにグラフ上のランダムなノードが割り当てられます。
  * `kwargs` : モデルプロパティとして使用されるキーワード引数。
