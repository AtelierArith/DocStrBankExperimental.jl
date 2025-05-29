```julia
DiffEqBase.OptimizationProblemExpr{iip}(sys::OptimizationSystem,
                                        parammap = DiffEqBase.NullParameters();
                                        u0 = nothing,
                                        grad = false,
                                        hes = false, sparse = false,
                                        checkbounds = false,
                                        linenumbers = true, parallel = SerialForm(),
                                        kwargs...) where {iip}
```

OptimizationSystemからOptimizationProblemのためのJulia式を生成し、数値的な強化を自動的に記号的に計算することを可能にします。
