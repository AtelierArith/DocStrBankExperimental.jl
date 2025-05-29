```
is_solved_and_feasible(
    model::GenericModel;
    allow_local::Bool = true,
    allow_almost::Bool = false,
    dual::Bool = false,
    result::Int = 1,
)
```

`true`を返す条件:

  * [`termination_status`](@ref) が以下のいずれかである場合:

      * [`OPTIMAL`](@ref) (ソルバーがグローバル最適解を見つけた)
      * [`LOCALLY_SOLVED`](@ref) (ソルバーがローカル最適解を見つけたが、それがグローバル最適解であることを証明できなかった)
  * 結果インデックス `result` の [`primal_status`](@ref) が `FEASIBLE_POINT` である場合。

この関数は保守的であり、ソルバーが時間制限により実行を終了した場合などには `false` を返します。

この関数が `false` を返した場合は、[`termination_status`](@ref)、[`result_count`](@ref)、[`primal_status`](@ref)、および [`dual_status`](@ref) を使用して、利用可能な解が何かを理解してください（もしあれば）。

関連情報: [`assert_is_solved_and_feasible`](@ref)。

## キーワード引数

### `allow_local`

`allow_local = false` の場合、この関数は [`termination_status`](@ref) が [`OPTIMAL`](@ref) の場合にのみ `true` を返します。

### `allow_almost`

`allow_almost = true` の場合、[`termination_status`](@ref) は追加で [`ALMOST_OPTIMAL`](@ref) または [`ALMOST_LOCALLY_SOLVED`](@ref) (もし `allow_local` が真であれば) である可能性があり、[`primal_status`](@ref) および [`dual_status`](@ref) は追加で [`NEARLY_FEASIBLE_POINT`](@ref) である可能性があります。

### `dual`

`dual` の場合、最適な双対解が [`dual_status`](@ref) を介して利用可能であることを追加で確認します。`allow_` キーワードは、プライマル解と双対解の両方を制御します。

### `result`

クエリする結果のインデックス。この値は、[`primal_status`](@ref) および [`dual_status`](@ref) の `result` キーワード引数に渡されます。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> is_solved_and_feasible(model)
false

julia> is_solved_and_feasible(
           model;
           allow_almost = true,
           dual = true,
           result = 2,
       )
false
```
