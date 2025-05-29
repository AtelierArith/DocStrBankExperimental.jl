```julia
DiffEqBase.ODEProblem{iip}(sys::AbstractODESystem, u0map, tspan,
                           parammap = DiffEqBase.NullParameters();
                           version = nothing, tgrad = false,
                           jac = false,
                           checkbounds = false, sparse = false,
                           simplify = false,
                           linenumbers = true, parallel = SerialForm(),
                           kwargs...) where {iip}
```

ODESystemからODEProblemを生成し、数値的な強化を自動的に記号的に計算することを可能にします。
