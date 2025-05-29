```julia
DiffEqBase.DAEProblem{iip}(sys::AbstractODESystem, du0map, u0map, tspan,
                           parammap = DiffEqBase.NullParameters();
                           version = nothing, tgrad = false,
                           jac = false,
                           checkbounds = false, sparse = false,
                           simplify = false,
                           linenumbers = true, parallel = SerialForm(),
                           kwargs...) where {iip}
```

ODESystemからDAEProblemを生成し、数値的な強化を自動的に記号的に計算することを可能にします。

注意: DAEProblems用のソルバー（DFBDF、DImplicitEuler、DABDF2など）は、一般的にODEProblems用のソルバーよりも遅くなります。最初にODEProblemとそのソルバーを試すことをお勧めします。
