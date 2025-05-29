```julia
struct SetPacking{ET, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

SetPacking(elements::AbstractVector, sets::AbstractVector, weights::AbstractVector=UnitWeight(length(sets))) -> SetPacking

パッキングは、各セットが互いに対してペアワイズに互いに素であるセットの集合です。最大（加重）パッキング問題は、与えられた和集合と部分集合のセットに対して最大パッキングを見つけることです。

## フィールド

  * `elements` は宇宙の要素のベクトルです。
  * `sets` はベクトルのベクトルであり、各セットは `weights` で指定された重みと関連付けられています。
  * `weights` はセットに関連付けられています。デフォルトでは `UnitWeight(length(sets))` です。

## 例

以下の例では、5つの部分集合を持つセットパッキング問題を定義します。`SetPacking` 問題を定義するには、部分集合のセットと、これらの部分集合に関連付けられた重みを指定する必要があります。重みは現在のバージョンではデフォルトで単位として設定されており、今後の開発で任意の正の重みに一般化される可能性があります。さらに、要素は構築関数によって自動的にカウントされます。

```jldoctest
julia> using ProblemReductions

julia> sets = [[1, 2, 5], [1, 3], [2, 4], [3, 6], [2, 3, 6]]
5-element Vector{Vector{Int64}}:
 [1, 2, 5]
 [1, 3]
 [2, 4]
 [3, 6]
 [2, 3, 6]

julia> SP = SetPacking(sets)
SetPacking{Int64, Int64, UnitWeight}([1, 2, 5, 3, 4, 6], [[1, 2, 5], [1, 3], [2, 4], [3, 6], [2, 3, 6]], [1, 1, 1, 1, 1])

julia> num_variables(SP)  # 自由度
5

julia> flavors(SP)  # 部分集合のフレーバー
(0, 1)

julia> solution_size(SP, [1, 0, 0, 1, 0]) # 正のサンプル: パッキングの -(サイズ)
SolutionSize{Int64}(2, true)

julia> solution_size(SP, [1, 0, 1, 1, 0]) # 負のサンプル: 0
SolutionSize{Int64}(3, false)

julia> findbest(SP, BruteForce())  # ブルートフォースで問題を解く
3-element Vector{Vector{Int64}}:
 [0, 1, 1, 0, 0]
 [1, 0, 0, 1, 0]
 [0, 0, 1, 1, 0]
```
