```
InterruptedConfidenceRegion(DM::AbstractDataModel, Confnum::Real; Boundaries::Union{Function,Nothing}=nothing, tol::Real=1e-9,
                            redo::Bool=true, meth::AbstractODEAlgorithm=Tsit5(), mfd::Bool=true, ADmode::Val=Val(:ForwardDiff), kwargs...) -> ODESolution
```

対数尤度のレベル線に沿って反時計回りに統合し、モデルが次のいずれかになるまで続けます。

1. `det(g) < tol` によって構造的に同定不可能になる
2. 指定された `Boundaries(u,t,int)` メソッドが `true` を評価する。

その後、この障害が発生した場所から時計回りに統合し、再びその障害に達するまで続け、半開の信頼区間を生成します。
