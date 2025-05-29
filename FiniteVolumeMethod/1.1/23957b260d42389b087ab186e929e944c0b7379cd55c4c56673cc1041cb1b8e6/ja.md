```
SteadyFVMProblem(prob::AbstractFVMProblem)
```

これは、問題が定常状態問題として解決されることを示す `AbstractFVMProblem` のラッパーです。次に、NonlinearSolve.jlから [`solve(::SteadyFVMProblem, ::Any; kwargs...)`](@ref) を使用して問題を解決できます。定常状態を無限大で出力したい場合は、最終時間を `Inf` に設定する必要があることに注意してください。実際の有限時間ではなく。

また、[`FVMProblem`](@ref) と [`FVMSystem`](@ref) も参照してください。
