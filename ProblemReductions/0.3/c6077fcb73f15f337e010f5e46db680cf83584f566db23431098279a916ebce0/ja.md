```julia
struct SetCovering{ET, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

セットカバリング問題は次のように定義されます：要素の宇宙と宇宙の部分集合のコレクションが与えられ、各セットには重みが関連付けられています。目標は、最小の総重みで全ての要素をカバーするセットの部分集合を見つけることです。

## 位置引数

  * `elements` は宇宙の要素のベクトルです。
  * `sets` はベクトルのベクトルで、宇宙の部分集合のコレクションであり、各セットには `weights` で指定された重みが関連付けられています。
  * `weights` はセットに関連付けられています。

## 例

以下の例では、3つの部分集合と重み `[1,2,3]` を持つセットカバリング問題を解決します。

```jldoctest
julia> using ProblemReductions

julia> subsets = [[1, 2, 3], [2, 4], [1, 4]]
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [2, 4]
 [1, 4]

julia> weights = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> setcovering = SetCovering(subsets, weights)
SetCovering{Int64, Int64, Vector{Int64}}([1, 2, 3, 4], [[1, 2, 3], [2, 4], [1, 4]], [1, 2, 3])

julia> num_variables(setcovering)  # 自由度
3

julia> solution_size(setcovering, [1, 0, 1])  # 構成のサイズ
SolutionSize{Int64}(4, true)

julia> solution_size(setcovering, [0, 1, 1])
SolutionSize{Int64}(5, false)

julia> sc = set_weights(setcovering, [1, 2, 3])  # 部分集合の重みを設定
SetCovering{Int64, Int64, Vector{Int64}}([1, 2, 3, 4], [[1, 2, 3], [2, 4], [1, 4]], [1, 2, 3])
```
