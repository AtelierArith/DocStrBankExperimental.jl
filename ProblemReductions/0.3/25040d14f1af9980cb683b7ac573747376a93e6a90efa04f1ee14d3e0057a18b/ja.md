```julia
struct PaintShop{LT} <: ProblemReductions.ConstraintSatisfactionProblem{Int64}
```

バイナリペイントショップ問題は次のように定義されます：$2m$の長さのシーケンスが与えられ、$m$台の車が含まれています。各車は2回現れます。各車は1回目に赤色に、もう1回目に青色に塗られる必要があります。各車のどの出現をどの色で塗るかを選択する必要があります — 目標は現在の色を変更する回数を最小限に抑えることです。

## フィールド

  * `sequence` はシンボルのベクターであり、各シンボルは色に関連付けられています。
  * `isfirst` はブール値のベクターであり、シンボルがシーケンス内で最初に現れるかどうかを示します。

## 例

以下の例では、6台の車を持つペイントショップ問題を定義します。

```jldoctest
julia> using ProblemReductions

julia> problem = PaintShop(["a","b","a","c","c","b"])
PaintShop{String}(["a", "b", "a", "c", "c", "b"], Bool[1, 1, 0, 1, 0, 0])

julia> num_variables(problem)
3

julia> flavors(problem)
(0, 1)

julia> solution_size(problem, [0, 1, 0])
SolutionSize{Int64}(4, true)

julia> findbest(problem, BruteForce())
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 1, 1]
```
