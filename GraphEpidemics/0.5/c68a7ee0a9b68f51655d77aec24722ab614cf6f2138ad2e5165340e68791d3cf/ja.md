`run_complex_contagion(model::AbstractEpiModel, g::AbstractGraph, T::Integer, rng::AbstractRNG, data::SimData; spreading_function::Function = is_spreading, verbose::Bool = false)`

ネットワーク上で固定された時間ステップ数にわたって感染の広がりをシミュレートします。

時間 `0` から `T` までの独立した遷移と広がりの遷移を適用し、シミュレーションの状態をその場で更新します。各タイムステップで各状態にあるノードの数を追跡する NamedTuples のベクターを返します。

### オプション引数

  * `spreading_function`: 隣接ノード間で感染が広がるかどうかを判断するカスタム関数。
  * `verbose`: true の場合、追加のデバッグ情報を印刷します。
