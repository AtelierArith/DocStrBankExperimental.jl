```julia
SciMLBase.SteadyStateProblemExpr(sys::AbstractODESystem, u0map,
                                 parammap = DiffEqBase.NullParameters();
                                 version = nothing, tgrad = false,
                                 jac = false,
                                 checkbounds = false, sparse = false,
                                 skipzeros = true, fillzeros = true,
                                 linenumbers = true, parallel = SerialForm(),
                                 kwargs...) where {iip}
```

ODEシステムからSteadyStateProblemを構築するためのJulia式を生成し、数値的な強化を自動的に記号的に計算することを可能にします。
