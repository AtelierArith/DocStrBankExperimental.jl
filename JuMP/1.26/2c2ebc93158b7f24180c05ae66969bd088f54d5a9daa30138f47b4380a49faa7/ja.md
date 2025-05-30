```
@constraint(model, expr, args...; kwargs...)
@constraint(model, [index_sets...], expr, args...; kwargs...)
@constraint(model, name, expr, args...; kwargs...)
@constraint(model, name[index_sets...], expr, args...; kwargs...)
```

式 `expr` で説明される制約を追加します。

`name` 引数はオプションです。インデックスセットが渡されると、コンテナが構築され、制約はインデックスセットのインデックスに依存する場合があります。

式 `expr` は以下の形式のいずれかである可能性があります：

  * `func in set` は、関数 `func` がセット `set` に属することを制約します。`set` は [`MOI.AbstractSet`](@ref) であるか、[`SecondOrderCone`](@ref) や [`PSDCone`](@ref) のような JuMP ショートカットのいずれかです。
  * `a <op> b` で、`<op>` は `==`、`≥`、`>=`、`≤`、`<=` のいずれかです。
  * `l <= f <= u` または `u >= f >= l` で、式 `f` が `l` と `u` の間にあることを制約します。
  * `f(x) ⟂ x` は、補完制約を定義します。
  * `z --> {expr}` は、`z` が `1` のときにアクティブになる指標制約を定義します。
  * `!z --> {expr}` は、`z` が `0` のときにアクティブになる指標制約を定義します。
  * `z <--> {expr}` は、再構成された制約を定義します。
  * `expr := rhs` は、ブール等式制約を定義します。

ブロードキャストされた比較演算子（例：`.==`）も、比較演算子の左辺と右辺が配列である場合にサポートされています。

JuMP 拡張は、ここにリストされていない制約式のサポートを追加で提供する場合があります。

## キーワード引数

  * `base_name`: 制約名を生成するために使用される名前プレフィックスを設定します。スカラー制約の制約名に対応し、それ以外の場合、制約名は各インデックス `...` に対して `base_name[...]` に設定されます。
  * `container = :Auto`: `container = Array`、`container = DenseAxisArray`、`container = SparseAxisArray`、または JuMP 拡張によってサポートされている他の任意のコンテナタイプを渡すことで、コンテナタイプを強制します。
  * `set_string_name::Bool = true`: [`MOI.ConstraintName`](@ref) 属性を設定するかどうかを制御します。`set_string_name = false` を渡すことでパフォーマンスを向上させることができます。

他のキーワード引数は JuMP 拡張によってサポートされる場合があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @variable(model, z, Bin);

julia> @constraint(model, x in SecondOrderCone())
[x[1], x[2], x[3]] ∈ MathOptInterface.SecondOrderCone(3)

julia> @constraint(model, [i in 1:3], x[i] == i)
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.EqualTo{Float64}}, ScalarShape}}:
 x[1] = 1
 x[2] = 2
 x[3] = 3

julia> @constraint(model, x .== [1, 2, 3])
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.EqualTo{Float64}}, ScalarShape}}:
 x[1] = 1
 x[2] = 2
 x[3] = 3

julia> @constraint(model, con_name, 1 <= x[1] + x[2] <= 3)
con_name : x[1] + x[2] ∈ [1, 3]

julia> @constraint(model, con_perp[i in 1:3], x[i] - 1 ⟂ x[i])
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.VectorAffineFunction{Float64}, MathOptInterface.Complements}, VectorShape}}:
 con_perp[1] : [x[1] - 1, x[1]] ∈ MathOptInterface.Complements(2)
 con_perp[2] : [x[2] - 1, x[2]] ∈ MathOptInterface.Complements(2)
 con_perp[3] : [x[3] - 1, x[3]] ∈ MathOptInterface.Complements(2)

julia> @constraint(model, z --> {x[1] >= 0})
z --> {x[1] ≥ 0}

julia> @constraint(model, !z --> {2 * x[2] <= 3})
!z --> {2 x[2] ≤ 3}
```
