デバイスのための抽象型で、[inject](@ref I) 電力または電流を供給します。

[static](@ref S) 注入は、一定の状態の注入であり、例えば、5分間一定に保たれた発電機の出力電力をモデル化することです。

多くの `StaticInjection` モデルは、[dynamic](@ref D) シミュレーションを行うためのオプションの追加として [`DynamicInjection`](@ref) モデルを受け入れることができます。
