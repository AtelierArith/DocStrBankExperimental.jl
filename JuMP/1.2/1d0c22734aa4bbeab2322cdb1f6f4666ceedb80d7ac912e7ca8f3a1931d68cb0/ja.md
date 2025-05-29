```
constraint_by_name(model::AbstractModel,
                   name::String)::Union{ConstraintRef, Nothing}
```

名前属性 `name` を持つ制約の参照を返すか、名前属性を持つ制約がない場合は `Nothing` を返します。複数の制約が `name` を名前属性として持つ場合はエラーをスローします。

```
constraint_by_name(model::AbstractModel,
                   name::String,
                   F::Type{<:Union{AbstractJuMPScalar,
                                   Vector{<:AbstractJuMPScalar},
                                   MOI.AbstactFunction}},
                   S::Type{<:MOI.AbstractSet})::Union{ConstraintRef, Nothing}
```

上記のメソッドと似ていますが、制約が `F`-in-`S` 制約でない場合はエラーをスローします。ここで `F` は JuMP または MOI の関数の型であり、`S` は MOI の集合の型です。関数と集合の型がわかっている場合は、このメソッドを推奨します。なぜなら、戻り値の型を推論できるからです。一方、上記のメソッド（`F` と `S` なし）では、制約インデックスの正確な戻り値の型を推論できません。

```jldoctest objective_function; setup = :(using JuMP), filter = r"Stacktrace:.*"s
julia> using JuMP

julia> model = Model()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> @variable(model, x)
x

julia> @constraint(model, con, x^2 == 1)
con : x² = 1.0

julia> constraint_by_name(model, "kon")

julia> constraint_by_name(model, "con")
con : x² = 1.0

julia> constraint_by_name(model, "con", AffExpr, MOI.EqualTo{Float64})

julia> constraint_by_name(model, "con", QuadExpr, MOI.EqualTo{Float64})
con : x² = 1.0
```
