```
ivp(expr...)
```

与えられた式に対応する初期値問題タイプのインスタンスを返します。

### 入力

  * `expr` – 動的方程式、制約集合、システムの次元、および初期状態のセットを定義するカンマで区切られた式（必須）

### 出力

与えられた式に最も適した初期値問題。

### 注意事項

このマクロは `@system` マクロのように動作しますが、唯一の違いは `@ivp` では初期状態のセットに対する制約が必須であることです。技術的な詳細については、[`@system`](@ref) のドキュメントを参照してください。

このマクロは、`AbstractSystem` 型の `system` 引数を `@ivp(system, state(0) ∈ initial_set)` の形式で呼び出すこともできます。

### 例

```jldoctest ivp_macro
julia> p = @ivp(x' = -x, x(0) ∈ [1.0]);

julia> typeof(p)
InitialValueProblem{LinearContinuousSystem{Float64, IdentityMultiple{Float64}}, Vector{Float64}}

julia> initial_state(p)
1-element Vector{Float64}:
 1.0

julia> sys = @system(x' = [1 0; 0 1] * x);

julia> @ivp(sys, x(0) ∈ [-1, 1])
InitialValueProblem{LinearContinuousSystem{Int64, Matrix{Int64}}, Vector{Int64}}(LinearContinuousSystem{Int64, Matrix{Int64}}([1 0; 0 1]), [-1, 1])
```
