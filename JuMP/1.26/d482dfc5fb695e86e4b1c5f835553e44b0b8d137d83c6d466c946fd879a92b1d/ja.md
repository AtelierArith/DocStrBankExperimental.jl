```
assert_is_solved_and_feasible(model::GenericModel; kwargs...)
```

関数は[`is_solved_and_feasible`](@ref)を呼び出し、戻り値が`false`の場合、ソルバーの状態を説明する情報メッセージでエラーを返します。

## キーワード引数

すべてのキーワード引数の説明については[`is_solved_and_feasible`](@ref)を参照してください。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> is_solved_and_feasible(model)
false

julia> assert_is_solved_and_feasible(model)
ERROR: モデルは正しく解決されませんでした。これが発生した理由をデバッグするための`solution_summary`の出力は次のとおりです：

solution_summary(; result = 1, verbose = false)
├ solver_name          : Ipopt
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION

Stacktrace:
[...]
```
