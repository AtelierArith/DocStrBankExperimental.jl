```
get_system(res, prob::PEtabODEProblem; kwargs...) -> (sys, p, u0, callbacks)
```

動的モデルシステム、パラメータマップ（`p`）、初期種マップ（`u0`）、およびコールバック（`CallbackSet`）を`prob`のモデルに対して取得します。引数`res`は、パラメータ推定結果（例：`PEtabMultistartResult`）または`prob`が期待する順序のパラメータの`Vector`であることができます（[`get_x`](@ref）を参照）。

返されるシステムタイプは、`PEtabModel`への入力に依存します。モデルが`ReactionSystem`として提供される場合、`ReactionSystem`が返されます。同様に、`ODESystem`の場合も同様です。モデルがSBMLファイルを介して提供される場合、`ReactionSystem`が返されます。

キーワード引数に関する情報は、[`get_ps`](@ref)を参照してください。

関連情報：[`get_u0`](@ref)および[`get_odesol`](@ref)。
