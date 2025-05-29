```
abstract type DiscreteModel{Dc,Dp} <: Grid
```

物理グリッド、基盤となるグリッドトポロジー、およびグリッドフェイスのラベリングに関する情報を保持する抽象型です。これは通常、メッシュジェネレーターが提供する情報であり、シミュレーションを実行するために必要なものです。

`DiscreteModel` インターフェースは、次のメソッドをオーバーロードすることで定義されます：

  * [`get_grid(model::DiscreteModel)`](@ref)
  * [`get_grid_topology(model::DiscreteModel)`](@ref)
  * [`get_face_labeling(g::DiscreteModel)`](@ref)

インターフェースは次の関数でテストされます：

  * [`test_discrete_model`](@ref)
