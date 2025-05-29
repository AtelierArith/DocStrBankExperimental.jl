```julia
kill_node!(
    node,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}}
) -> Union{Nothing, Int64}

```

モデルグラフからノードを削除します。パフォーマンスの理由から、この関数はノードが含まれているかどうかをチェックしないため、ユーザーが存在しないノードを削除しようとするとエラーが発生します。また、モデル内のエージェントが殺せない場合、かつ指定されたノードにエージェントが存在する場合、そのノードは削除されません。
