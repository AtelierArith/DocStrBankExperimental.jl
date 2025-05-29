```julia
DiffEqBase.NonlinearProblemExpr{iip}(sys::NonlinearSystem, u0map,
                                     parammap = DiffEqBase.NullParameters();
                                     jac = false, sparse = false,
                                     checkbounds = false,
                                     linenumbers = true, parallel = SerialForm(),
                                     kwargs...) where {iip}
```

非線形システムから非線形問題のためのJulia式を生成し、数値的な強化を自動的に記号的に計算することを可能にします。
