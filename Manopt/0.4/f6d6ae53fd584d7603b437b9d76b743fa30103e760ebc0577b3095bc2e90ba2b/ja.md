```
StopWhenChangeLess <: StoppingCriterion
```

は、最適化変数の変化のノルムを見続けるのを停止するしきい値を [`AbstractManoptSolverState`](@ref) から保存します。すなわち、`get_iterate(o)` です。保存には [`StoreStateAction`](@ref) が使用されます。

# コンストラクタ

```
StopWhenChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    inverse_retraction_method::IRT=default_inverse_retraction_method(manifold)
)
```

は、しきい値 `ε` に基づいて停止基準を初期化します。これは、デフォルトで `:Iterate` を保存するように初期化された [`StoreStateAction`](@ref) `a` を使用します。また、`distance` のための逆*引き戻し*メソッドや、デフォルトの逆引き戻しを使用するための多様体を提供することもできます。
