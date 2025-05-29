```julia
NonlinearProblem(f, u0; ...)
NonlinearProblem(f, u0, p; kwargs...)

```

[`AbstractODEFunction`](@ref AbstractODEFunction)のインスタンスを使用して非線形問題を定義します。これは定常状態問題の形で解釈され、すなわち、時間 $t = \infty$ におけるODEの解を見つけることを意味します。
