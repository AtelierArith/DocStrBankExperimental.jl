```julia
create_3d_model(
    agents::Array{EasyABM.Agent3D{S<:Union{Float64, Int64}, A<:EasyABM.SType, B<:EasyABM.MType}, 1};
    graphics,
    agents_type,
    size,
    random_positions,
    space_type,
    kwargs...
) -> Union{EasyABM.SpaceModel3D{EasyABM.StaticType, S, EasyABM.PeriodicType} where S<:Float64, EasyABM.SpaceModel3D{EasyABM.StaticType, S, EasyABM.PeriodicType} where S<:Int64}

```

3Dモデルを作成します。

  * `agents` : エージェントのリスト。
  * `graphics` : trueの場合、形状、色、向きのプロパティがデフォルトで各エージェントに割り当てられます。ユーザーがすでに割り当てていない場合。
  * `agents_type` : モデル実行中にエージェントの数が固定されている場合はStaticに設定します。そうでない場合はMortalに設定します。
  * `size` : 空間がx、y、z方向に分割されるブロックの数を示すタプル (dimx, dimy, dimz)。エージェントはx方向で0からdimx、y方向で0からdimy、z方向で0からdimzの位置を取ることができます。エージェントは、ユーザーがステップルールを実装する方法に応じて、連続的にまたは離散的なステップで移動できます（グリッドタイプのエージェントは離散的なステップでのみ移動できます）。空間の各ユニットブロックはパッチと呼ばれ、エージェントのように独自のプロパティを割り当てることができます。
  * `random_positions` : このプロパティがtrueの場合、各エージェントにランダムな位置が割り当てられます。
  * `space_type` : 空間が周期的かどうかに応じてPeriodicまたはNPeriodicに設定します。
  * `kwargs` : モデルプロパティとして使用されるキーワード引数。
