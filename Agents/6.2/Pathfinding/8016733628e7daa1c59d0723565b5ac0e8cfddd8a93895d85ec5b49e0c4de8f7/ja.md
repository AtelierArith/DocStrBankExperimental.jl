```
経路探索
```

A*アルゴリズムに基づく経路探索の機能を含むサブモジュール。現在、[`GridSpace`](@ref)および[`ContinuousSpace`](@ref)で利用可能です。[`ContinuousSpace`](@ref)の離散化は内部で処理されます。

[`Pathfinding.AStar`](@ref)構造体のインスタンスを作成することで、経路探索を有効にし、そのオプションを設定できます。これはシミュレーション中に関連する経路探索関数に渡す必要があります。エージェントの目的地を設定するには、[`plan_route!`](@ref)を呼び出します。これにより、エージェントの現在の位置から指定された位置までの経路を計算するアルゴリズムがトリガーされます。代わりに、リストから最適なターゲットを選択するには、[`plan_best_route!`](@ref)を使用できます。ターゲットが設定されると、[`move_along_route!`](@ref)関数を使用して、エージェントを事前に計算された経路に沿って1ステップ移動させることができます。

経路探索を使用した[迷路ソルバー](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/maze/)、[マウンテンランナー](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/runners/)および[ウサギ、キツネ、タカ](https://juliadynamics.github.io/Agents.jl/stable/examples/rabbit_fox_hawk/)の例を参照し、以下の利用可能な関数も確認してください。
