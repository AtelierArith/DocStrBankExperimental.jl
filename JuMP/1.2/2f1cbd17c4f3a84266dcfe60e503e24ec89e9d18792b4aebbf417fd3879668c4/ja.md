```
NLPEvaluator(
    model::Model,
    _differentiation_backend::MOI.Nonlinear.AbstractAutomaticDifferentiation =
        MOI.Nonlinear.SparseReverseMode(),
)
```

Return an [`MOI.AbstractNLPEvaluator`](@ref) constructed from `model`

!!! warning
    使用する前に、[`MOI.initialize`](@ref)を使用して評価者を初期化する必要があります。


## Experimental

これらの機能は、今後のJuMPのバージョンで変更または削除される可能性があります。

微分を計算するために使用される微分バックエンドを指定するには、`_differentiation_backend`を渡します。
