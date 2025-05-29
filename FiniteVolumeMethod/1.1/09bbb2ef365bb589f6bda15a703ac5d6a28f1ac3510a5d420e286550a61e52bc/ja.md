```
solve(prob::SteadyFVMProblem, alg; 
    specialization=SciMLBase.AutoSpecialize, 
    jac_prototype=jacobian_sparsity(prob),
    parallel::Val{<:Bool}=Val(true),
    kwargs...)
```

与えられた [`FVMProblem`](@ref) または [`FVMSystem`](@ref) `prob` をアルゴリズム `alg` で解きます。

# 引数

  * `prob`: 解決すべき問題。
  * `alg`: 問題を解くために使用されるアルゴリズム。これは NonlinearSolve.jl のアルゴリズムのいずれかであることができます。

# キーワード引数

  * `specialization=SciMLBase.AutoSpecialize`: 使用される特殊化のタイプ。詳細は https://docs.sciml.ai/DiffEqDocs/stable/features/low_dep/#Controlling-Function-Specialization-and-Precompilation を参照してください。
  * `jac_prototype=jacobian_sparsity(prob)`: デフォルトで `jacobian_sparsity` から構築されたヤコビ行列のプロトタイプ。
  * `parallel::Val{<:Bool}=Val(true)`: マルチスレッドを使用するかどうか。マルチスレッドを無効にするには `Val(false)` を使用します。
  * `kwargs...`: ソルバーに渡されるその他のキーワード引数。

# 出力

返される値 `sol` は、基盤となる問題が [`FVMProblem`](@ref) か [`FVMSystem`](@ref) かによって異なりますが、いずれの場合も DifferentialEquations.jl の解のようにアクセスできる `ODESolution` 型です：

  * [`FVMProblem`](@ref)

この場合、`sol` は `i` 番目のコンポーネントが基盤となるメッシュの `i` 番目のノードを参照します。

  * [`FVMSystem`](@ref)

この場合、`sol` の `(j, i)` 番目のコンポーネントは、システムの `j` 番目のコンポーネントに対する基盤となるメッシュの `i` 番目のノードを参照します。
