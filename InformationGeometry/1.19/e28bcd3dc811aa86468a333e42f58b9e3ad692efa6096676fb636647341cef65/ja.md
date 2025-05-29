```
IsLinear(DM::DataModel, MLE::AbstractVector) -> Bool
```

`model(x,θ)` 関数がすべてのパラメータ $\theta \in \mathcal{M}$ に関して線形であるかどうかをチェックします。成分ごとのチェックは、メソッド `IsLinearParameter(DM)` を通じて達成できます。
