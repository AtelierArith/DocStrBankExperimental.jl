シミュレーションのCarlo内部状態を保持し、次のインターフェースを提供します。

  * **乱数**: 公開フィールド `MCContext.rng` は乱数生成器です（[rng](@ref)を参照）。
  * **測定**: [`measure!(::MCContext, ::Symbol, ::Any)`](@ref)を参照。
  * **シミュレーション状態**: [`is_thermalized`](@ref)を参照。
