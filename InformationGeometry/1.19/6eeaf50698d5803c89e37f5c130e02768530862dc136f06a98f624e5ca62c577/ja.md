```
ParameterSavingCallback(start::AbstractVector) -> (Vector{typeof(start)}, Function)
```

最初のエントリが空の `Vector{typeof(start)}` 配列を構成し、パラメータの軌跡が保存されます。第二のエントリはコールバック関数自体であり、`callback` キーワード引数を介して最適化手法に追加されます。

# 例

```julia
Pars, Func = ParameterSavingCallback(MLE(DM))
InformationGeometry.minimize(DM, rand(3); meth=Optim.NewtonTrustRegion(), OptimJL=false, callback=Func)
TracePlot(Pars)
```

!!! 注     Optim.jl の最適化器には、OptimizationOptimJL.jl でラップしない限り機能しません。つまり、キーワード `OptimJL=false` を設定する必要があります。
