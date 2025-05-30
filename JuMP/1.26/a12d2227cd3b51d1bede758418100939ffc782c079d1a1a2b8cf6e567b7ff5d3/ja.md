```
relax_with_penalty!(
    model::GenericModel{T},
    [penalties::Dict{ConstraintRef,T}];
    [default::Union{Nothing,Real} = nothing,]
) where {T}
```

モデルを破壊的にインプレースで変更して、制約のペナルティ付き緩和を作成します。

!!! warning
    これはモデルをインプレースで変更する破壊的なルーチンです。元のモデルを変更したくない場合は、[`relax_with_penalty!`](@ref)を呼び出す前に[`copy_model`](@ref)を使用してコピーを作成してください。


## 再定式化

再定式化の詳細については、[`MOI.Utilities.ScalarPenaltyRelaxation`](@ref)を参照してください。

各制約 `ci` に対して、[`MOI.Utilities.ScalarPenaltyRelaxation`](@ref) に渡されるペナルティは `get(penalties, ci, default)` です。値が `nothing` の場合、`ci` が `penalties` に存在せず、`default = nothing` であるため、制約はスキップされます。

## 戻り値

この関数は、各制約インデックスを対応する `y + z` とマッピングする `Dict{ConstraintRef,AffExpr}` を返します。最適解では、これらの関数の値を照会して各制約の違反を計算します。

## 制約のサブセットを緩和する

制約のサブセットを緩和するには、`penalties` 辞書を渡し、`default = nothing` を設定します。

## 例

```jldoctest
julia> function new_model()
           model = Model()
           @variable(model, x)
           @objective(model, Max, 2x + 1)
           @constraint(model, c1, 2x - 1 <= -2)
           @constraint(model, c2, 3x >= 0)
           return model
       end
new_model (generic function with 1 method)

julia> model_1 = new_model();

julia> penalty_map = relax_with_penalty!(model_1; default = 2.0);

julia> penalty_map[model_1[:c1]]
_[3]

julia> penalty_map[model_1[:c2]]
_[2]

julia> print(model_1)
Max 2 x - 2 _[2] - 2 _[3] + 1
Subject to
 c2 : 3 x + _[2] ≥ 0
 c1 : 2 x - _[3] ≤ -1
 _[2] ≥ 0
 _[3] ≥ 0

julia> model_2 = new_model();

julia> relax_with_penalty!(model_2, Dict(model_2[:c2] => 3.0))
Dict{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.GreaterThan{Float64}}, ScalarShape}, AffExpr} with 1 entry:
  c2 : 3 x + _[2] ≥ 0 => _[2]

julia> print(model_2)
Max 2 x - 3 _[2] + 1
Subject to
 c2 : 3 x + _[2] ≥ 0
 c1 : 2 x ≤ -1
 _[2] ≥ 0
```
