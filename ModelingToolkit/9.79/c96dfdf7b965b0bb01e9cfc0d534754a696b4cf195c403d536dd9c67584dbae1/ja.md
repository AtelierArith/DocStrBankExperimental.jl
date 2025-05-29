```julia
DiffEqBase.OptimizationProblem{iip}(sys::OptimizationSystem, u0map,
                                    parammap = DiffEqBase.NullParameters();
                                    grad = false,
                                    hess = false, sparse = false,
                                    cons_j = false, cons_h = false,
                                    checkbounds = false,
                                    linenumbers = true, parallel = SerialForm(),
                                    kwargs...) where {iip}
```

OptimizationSystemからOptimizationProblemを生成し、数値的な強化を自動的に記号的に計算することを可能にします。

特定のソルバーは、制約付き最適化問題のために`cons_j`、`cons_h`を`true`に設定する必要があります。
