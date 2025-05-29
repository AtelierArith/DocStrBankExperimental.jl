```
SemialgebraicSetsHCSolver(; excess_residual_tol = nothing, real_tol = 1e-6, compile = false, options...)
```

`SemialgebraicSets`で使用するための`SemialgebraicSets.AbstractAlgebraicSolver`を構築します。`options`は[`solve`](@ref)のすべての有効なオプションです。

絶対値が`real_tol`より大きい虚部を持つ解はフィルタリングされます。

過剰決定系の場合、`excess_residual_tol`を`Float64`値に設定できます。残差が`excess_residual_tol`より小さい過剰解は成功として再考されます。

## 例

```
julia> using HomotopyContinuation, SemialgebraicSets;

julia> solver = SemialgebraicSetsHCSolver(; show_progress = false)
SemialgebraicSetsHCSolver(; compile = :none, show_progress = false)

julia> @polyvar x y
(x, y)

julia> V = @set x^2 == 1 && y^2 == 2 solver
代数的集合 2つの等式によって定義される
 x^2 - 1.0 = 0
 y^2 - 2.0 = 0

julia> collect(V)
4-element Array{Array{Float64,1},1}:
 [1.0, 1.414213562373095]
 [1.0, -1.414213562373095]
 [-1.0, 1.414213562373095]
 [-1.0, -1.414213562373095]
```
