他のシステムを一緒に構成するためのシステム [`couple`](@ref) 関数を使用します。

  * `systems`: 一緒に構成されるモデルコンポーネント
  * `domaininfo`: 初期条件、境界条件、およびその他のドメイン情報
  * `pdefunctions`: 各関数がこのシステムに DomainInfo が追加された後の結果の PDESystem を引数として受け取り、変換された PDESystem を返す関数のベクトル。
  * `ops`: シミュレーション中に実行される演算子のベクトル。
  * `callbacks`: シミュレーション中に実行されるコールバックのベクトル。
  * `init_callbacks`: `init_callback(x, Simulator)::DECallback` メソッドを持つオブジェクト `x`。

`CoupledSystem` に追加できるもの：

  * `ModelingToolkit.ODESystem`。 ODESystem に `:coupletype` というメタデータのフィールドがある場合（例: `ModelingToolkit.get_metadata(sys)[:coupletype]` が `sys` という単一フィールドを持つ構造体型を返す）、その型が `EarthSciMLBase.couple` のメソッドをチェックするために使用されます。
  * [`Operator`](@ref)
  * [`DomainInfo`](@ref)
  * [コールバック](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/)
  * `EarthSciMLBase.init_callback(::X, ::CoupledSystem, sys_mtk, ::DomainInfo, ::MapAlgorithm)::DECallback` メソッドを実装する型 `X`
  * その他の `CoupledSystem`
  * `EarthSciMLBase.couple2(::X, ::CoupledSystem)` または `EarthSciMLBase.couple2(::CoupledSystem, ::X)` メソッドを実装する型 `X`。
  * 上記のいずれかのものの `Tuple` または `AbstractVector`。
