```julia
debug_system(sys)

```

特異点を持つ関数を、シンボリック情報でエラーを返す関数に置き換えます。例えば、

```julia-repl
julia> sys = debug_system(sys);

julia> prob = ODEProblem(sys, [], (0, 1.0));

julia> du = zero(prob.u0);

julia> prob.f(du, prob.u0, prob.p, 0.0)
ERROR: DomainError with (-1.0,):
log errors with input(s): -cos(Q(t)) => -1.0
Stacktrace:
  [1] (::ModelingToolkit.LoggedFun{typeof(log)})(args::Float64)
  ...
```
