```
constraint_by_name(model::AbstractModel, name::String, [F, S])::Union{ConstraintRef,Nothing}
```

名前属性 `name` を持つ制約の参照を返すか、その名前属性を持つ制約がない場合は `Nothing` を返します。

複数の制約が `name` を名前属性として持つ場合はエラーをスローします。

`F` と `S` が提供されている場合、このメソッドは制約が `F`-in-`S` 制約でない場合にエラーを追加でスローします。ここで `F` は関数の JuMP または MOI 型であり、`S` は集合の MOI 型です。

関数と集合の型が分かっている場合は、`F` と `S` を提供することをお勧めします。なぜなら、その返される型を推論できるからです。一方、上記のメソッド（つまり、`F` と `S` なし）では、制約インデックスの正確な返り値の型を推論することはできません。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, x^2 == 1)
con : x² = 1

julia> constraint_by_name(model, "kon")

julia> constraint_by_name(model, "con")
con : x² = 1

julia> constraint_by_name(model, "con", AffExpr, MOI.EqualTo{Float64})

julia> constraint_by_name(model, "con", QuadExpr, MOI.EqualTo{Float64})
con : x² = 1
```
