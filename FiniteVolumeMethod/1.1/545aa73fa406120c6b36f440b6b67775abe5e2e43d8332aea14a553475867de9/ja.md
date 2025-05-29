```
solve(prob::Union{FVMProblem,FVMSystem}, alg; 
    specialization=SciMLBase.AutoSpecialize, 
    jac_prototype=jacobian_sparsity(prob), 
    parallel::Val{<:Bool}=Val(true),
    kwargs...)
```

与えられた [`FVMProblem`](@ref) または [`FVMSystem`](@ref) `prob` をアルゴリズム `alg` で解きます。

!!! warning "欠落している頂点"
    基になる三角形分割 `tri` の `get_points(tri)` に、三角形分割自体の頂点でない点が含まれている場合、これらの点での解の関連値はソルバーによって更新されず、初期値のままとなります。


# 引数

  * `prob`: 解決すべき問題。
  * `alg`: 問題を解くために使用されるアルゴリズム。これは、DifferentialEquations.jl のアルゴリズムのいずれかであることができます。

# キーワード引数

  * `specialization=SciMLBase.AutoSpecialize`: 使用される特殊化のタイプ。詳細は https://docs.sciml.ai/DiffEqDocs/stable/features/low_dep/#Controlling-Function-Specialization-and-Precompilation を参照してください。
  * `jac_prototype=jacobian_sparsity(prob)`: デフォルトで `jacobian_sparsity` から構築されたヤコビ行列のプロトタイプ。
  * `parallel::Val{<:Bool}=Val(true)`: マルチスレッドを使用するかどうか。マルチスレッドを無効にするには `Val(false)` を使用します。
  * `kwargs...`: ソルバーに渡されるその他のキーワード引数。

# 出力

返される値 `sol` は問題のタイプによって異なります。

  * [`FVMProblem`](@ref)

この場合、`sol::ODESolution` は `sol` の `i` 番目のコンポーネントが基になるメッシュの `i` 番目のノードを参照します。

  * [`FVMSystem`](@ref)

この場合、`sol::ODESolution` の `(j, i)` 番目のコンポーネントは、システムの `j` 番目のコンポーネントに対する基になるメッシュの `i` 番目のノードを参照します。
