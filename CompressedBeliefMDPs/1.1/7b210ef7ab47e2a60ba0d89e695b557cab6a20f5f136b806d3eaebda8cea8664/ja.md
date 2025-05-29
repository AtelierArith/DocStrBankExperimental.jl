```
CompressedBeliefSolver
```

`CompressedBeliefSolver`構造体は、圧縮された信念状態MDPのソルバーを表します。これは、圧縮された信念状態MDPとベースソルバーを組み合わせて、価値関数を近似します。

## フィールド

  * `m::CompressedBeliefMDP`: 圧縮された信念状態MDP。
  * `base_solver::Solver`: 圧縮された信念状態MDPを解くために使用されるベースソルバー。

## コンストラクタ

```
CompressedBeliefSolver(pomdp::POMDP, base_solver::Solver; updater::Updater=DiscreteUpdater(pomdp), sampler::Sampler=BeliefExpansionSampler(pomdp), compressor::Compressor=PCACompressor(1))
CompressedBeliefSolver(pomdp::POMDP; updater::Updater=DiscreteUpdater(pomdp), sampler::Sampler=BeliefExpansionSampler(pomdp), compressor::Compressor=PCACompressor(1), interp::Union{Nothing, LocalFunctionApproximator}=nothing, k::Int=1, verbose::Bool=false, max_iterations::Int=1000, n_generative_samples::Int=10, belres::Float64=1e-3)
```

指定されたPOMDP、ベースソルバー、アップデーター、サンプラー、およびコンプレッサーを使用して`CompressedBeliefSolver`を構築します。代わりに、ベースソルバーを省略することもでき、その場合は`LocalApproximationValueIterationSolver`(https://github.com/JuliaPOMDP/LocalApproximationValueIteration.jl)が代わりに作成されます。たとえば、POMDPの状態とアクション空間が連続している場合は、異なるベースソルバーが必要です。

## 使用例

```julia-repl
julia> pomdp = TigerPOMDP();
julia> solver = CompressedBeliefSolver(pomdp; verbose=true, max_iterations=10);
julia> solve(solver, pomdp);
[Iteration 1   ] residual:       8.51 | iteration runtime:    635.870 ms, (     0.636 s total)
[Iteration 2   ] residual:       3.63 | iteration runtime:      0.504 ms, (     0.636 s total)
[Iteration 3   ] residual:       10.1 | iteration runtime:      0.445 ms, (     0.637 s total)
[Iteration 4   ] residual:       15.2 | iteration runtime:      0.494 ms, (     0.637 s total)
[Iteration 5   ] residual:       6.72 | iteration runtime:      0.432 ms, (     0.638 s total)
[Iteration 6   ] residual:       7.38 | iteration runtime:      0.508 ms, (     0.638 s total)
[Iteration 7   ] residual:       6.03 | iteration runtime:      0.495 ms, (     0.639 s total)
[Iteration 8   ] residual:       5.73 | iteration runtime:      0.585 ms, (     0.639 s total)
[Iteration 9   ] residual:       4.02 | iteration runtime:      0.463 ms, (      0.64 s total)
[Iteration 10  ] residual:       7.28 | iteration runtime:      0.576 ms, (      0.64 s total)
```
